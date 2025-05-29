```
fitted_params(signature; supplement=true)
```

**プライベートメソッド。**

`signature` に関連付けられた学習ネットワークのための fitted*params を生成し、補足の fitted*params を含めます。

`supplement=false` を指定することで、`signature` の fitted_params ノードの呼び出しを抑制し、それらの出力への寄与を除外します。

[`MLJBase.fitted_params_supplement`](@ref) も参照してください。

[`MLJBase.Signature`](@ref) も参照してください。
