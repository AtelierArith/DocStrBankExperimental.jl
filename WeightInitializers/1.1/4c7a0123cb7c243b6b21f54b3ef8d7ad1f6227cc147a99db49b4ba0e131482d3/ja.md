```
kaiming_uniform([::AbstractRNG=Utils.default_rng()], [T=Float32], size...;
    gain = √T(2)) -> AbstractArray{T, length(size)}
```

与えられた `size` の `AbstractArray{T}` を返し、`[-x, x]` の区間から引かれたランダムな数値を含みます。ここで、`x = gain * sqrt(3/fan_in)` です。

# 参考文献

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
