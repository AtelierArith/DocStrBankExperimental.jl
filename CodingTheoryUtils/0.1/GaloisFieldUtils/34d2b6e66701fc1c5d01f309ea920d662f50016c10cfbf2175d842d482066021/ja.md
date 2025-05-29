```
F2p(Fe::Type{<:GaloisFields.AbstractExtensionField}, b::Vector{Fb})::Fe
```

F2の要素のベクトルをフィールドの原始要素を使用してフィールド要素に変換します。

# 引数

  * `Fe::Type{<:GaloisFields.AbstractExtensionField}`: 対象のフィールドタイプ
  * `b::Vector{Fb}`: F2要素のベクトル

# 戻り値

  * `Fe`: ベクトルで表されるフィールド要素

# 例外

  * `AssertionError`: 入力ベクトルの長さがフィールドの拡張次数と一致しない場合

# 例

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> F2p(F4, [F2(1), F2(0)])
1
```
