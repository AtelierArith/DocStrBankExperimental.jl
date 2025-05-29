```
glorot_normal([::AbstractRNG=Utils.default_rng()], [T=Float32], size...;
    gain = 1) -> AbstractArray{T, length(size)}
```

与えられた `size` の `AbstractArray{T}` を返し、標準偏差 `gain * sqrt(2 / (fan_in + fan_out))` の正規分布から抽出されたランダムな数値を含みます。このメソッドは [1] で説明されており、Xavier 初期化としても知られています。

# 参考文献

[1] Glorot, Xavier, and Yoshua Bengio. "Understanding the difficulty of training deep feedforward neural networks." *Proceedings of the thirteenth international conference on artificial intelligence and statistics*. 2010.
