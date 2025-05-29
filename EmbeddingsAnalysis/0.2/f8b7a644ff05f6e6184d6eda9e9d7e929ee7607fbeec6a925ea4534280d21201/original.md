```
pca_reduction(wv::WordVectors, rdim=7, outdim=size(wv.vectors,1); [do_pca=true])
```

Post-processes word embeddings `wv` by removing the first `rdim` PCA components from the word vectors and also reduces the dimensionality to `outdim` through a subsequent PCA transform, if `do_pca=true`.

# Arguments

  * `wv::WordVectors` the word embeddings
  * `rdim::Int` the number of PCA components to remove from the data  (default 7)
  * `outdim::Int` the output dimensionality of the data after the PCA  dimensionality reduction; it is performed only if `do_pca=true`  and the default value is the same as that of the input embeddings  i.e. no reduction

# Keyword arguments

  * `do_pca::Bool` whether to perform a PCA transform of the  post-processed data (default `true`)

# References:

  * [Vikas Raunak "Simple and effective dimensionality reduction for  word embeddings", NIPS 2017 Workshop](https://arxiv.org/abs/1708.03629)
