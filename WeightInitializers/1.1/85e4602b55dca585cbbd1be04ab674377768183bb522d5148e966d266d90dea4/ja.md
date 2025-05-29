```
kaiming_normal([::AbstractRNG=Utils.default_rng()], [T=Float32], size...;
    gain = √T(2)) -> AbstractArray{T, length(size)}
```

与えられた `size` の `AbstractArray{T}` を返し、標準偏差 `gain / sqrt(fan_in)` の正規分布から取得したランダムな数値を含みます。

# 参考文献

[1] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." *Proceedings of the IEEE international conference on computer vision*. 2015.
