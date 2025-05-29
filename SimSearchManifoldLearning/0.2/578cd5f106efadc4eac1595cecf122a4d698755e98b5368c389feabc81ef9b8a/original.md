```
fit(UMAP::UMAP, maxoutdim; <kwargs>)
```

Reuses a previously computed model with a different number of components

# Keyword arguments

  * `n_epochs=50`: number of epochs to run
  * `learning_rate::Real = 1f0`: initial learning rate
  * `learning_rate_decay::Real = 0.9f0`: how learning rate is adjusted per epoch `learning_rate *= learning_rate_decay`
  * `repulsion_strength::Float32 = 1f0`: repulsion force (for negative sampling)
  * `neg_sample_rate::Integer = 5`: how many negative examples per object are used.
  * `tol::Real = 1e-4`: tolerance to early stopping while optimizing embeddings.
  * `minbatch=0`: controls how parallel computation is made. See [`SimilaritySearch.getminbatch`](@ref) and `@batch` (`Polyester` package).
