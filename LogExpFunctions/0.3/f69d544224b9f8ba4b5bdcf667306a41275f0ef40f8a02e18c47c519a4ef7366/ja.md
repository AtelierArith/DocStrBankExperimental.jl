```julia
softplus(x)

```

一般化された `softplus` 関数 (Wiemann et al., 2024) は、線形スプラインに関する近似誤差を制御する追加のオプションパラメータ `a` を取ります。デフォルトは `a=1.0` で、この場合、softplus は [`log1pexp`](@ref) と同等です。

参照:

  * Wiemann, P. F., Kneib, T., & Hambuckers, J. (2024). Using the softplus function to construct alternative link functions in generalized linear models and beyond. Statistical Papers, 65(5), 3155-3180.
