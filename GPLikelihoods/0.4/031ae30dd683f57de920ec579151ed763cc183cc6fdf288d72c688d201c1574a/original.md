```
BijectiveSimplexLink(link)
```

Wrapper to preprocess the inputs by adding a `0` at the end before passing it to  the link `link`. This is a necessary step to work with simplices. For example with the [`SoftMaxLink`](@ref), to obtain a `n`-simplex leading to `n+1` categories for the [`CategoricalLikelihood`](@ref), one needs to pass `n+1` latent GP. However, by wrapping the link into a `BijectiveSimplexLink`, only `n` latent are needed. 
