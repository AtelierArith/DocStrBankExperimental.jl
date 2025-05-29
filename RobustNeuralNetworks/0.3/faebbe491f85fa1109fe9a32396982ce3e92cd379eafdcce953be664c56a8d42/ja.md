```
direct_to_explicit(ps::AbstractRENParams{T}) where T
```

LBDNの直接パラメータ化を明示的パラメータ化に変換します。

`ps`にエンコードされたパラメータ化を使用して、ユーザー定義のリプシッツ境界を自然に尊重する[`ExplicitLBDNParams`](@ref)オブジェクトを構築します。

# 引数

  * `ps::AbstractLBDNParams`: モデル評価のために明示的パラメータ化に変換するLBDNの直接パラメータ化（例: [`DenseLBDNParams`](@ref)）。

他にも[`DenseLBDNParams`](@ref)を参照してください。
