```
generate(error_model, code, p::Real, [rng::AbstractRNG=GLOBAL_RNG]) -> BitVector
```

`error_model` と `code` に従って、バイナリシンプレクティック形式で新しいエラーを生成します。ここで `p` は通常、単一のキュービットでのエラーの確率です。

!!! note "抽象メソッド"
    このメソッドは、具体的なサブタイプまたは [`ErrorModel`](@ref) のダックタイピング実装のために実装されるべきです。

