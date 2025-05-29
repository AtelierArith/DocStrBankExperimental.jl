```
glorot_uniform([::AbstractRNG=Utils.default_rng()], [T=Float32], size...;
    gain = 1) -> AbstractArray{T, length(size)}
```

与えられた `size` の `AbstractArray{T}` を返し、$[-x, x]$ の区間から引かれたランダムな数値を含みます。ここで `x = gain * \sqrt{6 / (fan_in + fan_out)}$ です。このメソッドは[1]で説明されており、Xavier初期化としても知られています。

# 参考文献

[1] Glorot, Xavier, and Yoshua Bengio. "Understanding the difficulty of training deep feedforward neural networks." *Proceedings of the thirteenth international conference on artificial intelligence and statistics*. 2010.
