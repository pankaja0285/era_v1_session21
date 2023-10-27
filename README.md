<h1> Bigram Language Model
<h2> Training GPT model from scratch </h2>
<p>
Libraries used:
- torch <br/>
- numpy <br/>
- pandas <br/>
</p>
<p>
Set up: <br/>
- Data source is set up by downloading from !wget https://raw.githubusercontent.com/karpathy/char-rnn/master/data/tinyshakespeare/input.txt <br/>
- Proceed to setting up training and validation data  <br/>
- Train with a BigramLanguage Model architecture using Attention mechanism <br/>
</p>
<br/>
<p>
File structure: <br/>
__ README.md <br/>
__ S21_GPTFromScratch_Andrej_v1.ipynb<br/>
</p>
<h2> Steps: </h2>
<p>The notebook S21_GPTFromScratch_Andrej_v1.ipynb is self explanatory, all one needs to do is run the cells in sequence, <br/>
  irrespective of which environment you are running from Colab, or otherwise
</p>
<h2>Some background:</h2>
<p>
  Notes:
- Attention is a **communication mechanism**. Can be seen as nodes in a directed graph looking at each other and aggregating information with a weighted sum from all nodes that point to them, with data-dependent weights.
- There is no notion of space. Attention simply acts over a set of vectors. This is why we need to positionally encode tokens.
- Each example across batch dimension is of course processed completely independently and never "talk" to each other
- In an "encoder" attention block just delete the single line that does masking with `tril`, allowing all tokens to communicate. This block here is called a "decoder" attention block because it has triangular masking, and is usually used in autoregressive settings, like language modeling.
- "self-attention" just means that the keys and values are produced from the same source as queries. In "cross-attention", the queries still get produced from x, but the keys and values come from some other, external source (e.g. an encoder module)
- "Scaled" attention additional divides `wei` by 1/sqrt(head_size). This makes it so when input Q,K are unit variance, wei will be unit variance too and Softmax will stay diffuse and not saturate too much. Illustration below
</p>
<h3>Acknoledgements: This is based on Andrej Karpathy's training GPT from scratch and his YouTube video</h3>
<h4>Collaborators: GK Divya and Pankaja Shankar. Any questions or comments please drop a line.</h4>
