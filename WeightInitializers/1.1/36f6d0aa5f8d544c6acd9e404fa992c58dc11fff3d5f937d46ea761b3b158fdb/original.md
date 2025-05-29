```
glorot_normal([::AbstractRNG=Utils.default_rng()], [T=Float32], size...;
    gain = 1) -> AbstractArray{T, length(size)}
```

Return an `AbstractArray{T}` of the given `size` containing random numbers drawn from a normal distribution with standard deviation `gain * sqrt(2 / (fan_in + fan_out))`. This method is described in [1] and also known as Xavier initialization.

# References

[1] Glorot, Xavier, and Yoshua Bengio. "Understanding the difficulty of training deep feedforward neural networks." *Proceedings of the thirteenth international conference on artificial intelligence and statistics*. 2010.
