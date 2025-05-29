```
similarity_order(wv::WordVectors, alpha=-0.65)
```

Post-processes the word embeddings `wv` so that the embeddings capture more information than directly apparent through a linear transformation that adjusts the similarity order of the model. The function returns a new `WordVectors` object containing the processed embeddings.

# Arguments

  * `wv::WordVectors` the word embeddings

# `alpha::AbstractFloat` the `α` parameter of the algorithm (default -0.65)

# References:

  * [Artetxe et al. "Uncovering divergent linguistic information in  word embeddings with lessons for intrinsic and extrinsic evaluation",  2018](https://arxiv.org/pdf/1809.02094.pdf)
