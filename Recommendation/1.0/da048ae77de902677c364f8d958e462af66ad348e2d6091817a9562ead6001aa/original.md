```
generate(n_samples::Integer, n_items::Integer, features::AbstractVector{SyntheticFeature}, rules::AbstractVector{SyntheticRule}) -> DataAccessor
```

Generate a synthetic data accessor from randomly sampled implicit feedback. Each sample is considered as a different user, and user attributes are represented by a numeric onehot-encoded feature vector based on the values returned by `SyntheticFeature`.

The process is based on Section 7.3 of the following paper:

  * M. Aharon, et al. **OFF-Set: One-pass Factorization of Feature Sets for Online Recommendation in Persistent Cold Start Settings**. [arXiv:1308.1792](https://arxiv.org/abs/1308.1792).

```julia
n_samples = 256
n_items = 5
data = generate(n_samples, n_items, features, rules)
```
