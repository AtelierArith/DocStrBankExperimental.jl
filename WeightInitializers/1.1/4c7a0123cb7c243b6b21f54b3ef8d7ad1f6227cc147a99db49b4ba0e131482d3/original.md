```
kaiming_uniform([::AbstractRNG=Utils.default_rng()], [T=Float32], size...;
    gain = √T(2)) -> AbstractArray{T, length(size)}
```

Return an `AbstractArray{T}` of the given `size` containing random numbers drawn from a uniform distribution on the interval `[-x, x]`, where `x = gain * sqrt(3/fan_in)`.

# References

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
