```
rand([rng=GLOBAL_RNG, T_rng=Float64,] mc::ModelClosure)
```

Draw a sample from the model closure `mc`. There are two optional arguments:

1. `rng` specifies an `AbstractRNG` to use for sampling
2. `T_rng` specifies a type to pass to the inner call to `rand`. This makes it easy to sample using types other than the default `Float64`.

Note that `mc` must be a closure (a model with specified arguements). In particular, calling `rand` on a `ModelPosterior` (a closure with conditioning) is disallowed. To ignore the conditioning for some `post::ModelPosterior`, you can use `rand(post.closure)`.

Also note that a model closure is considered to be a measure on its *latent space*. That is, any return value in the model is ignored by `rand`. Use `predict` if you want the return value instead of a point in the latent space.
