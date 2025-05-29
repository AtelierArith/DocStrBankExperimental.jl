```
lohi(::Type{TN}, lo, hi) where TN<:ThickNumber
```

`lo` と `hi` の値から `TN` を構築します。

# インターフェース要件

`lohi` はすべての ThickNumber サブタイプによって実装されなければなりません。

もし

```julia
x = lohi(TN, lo, hi)
```

がエラーを投げずに成功する場合、次のことが要求されます。

```julia
typeof(x) <: TN
lo ∈ x
hi ∈ x
lo ≈ loval(x)
hi ≈ hival(x)
```

後者の2つについては、正確な等価性は要求されません。これは、`TN` が `lo` と `hi` の値以外のものでパラメータ化されている場合の丸め誤差や、保守的であり、丸め誤差が存在する場合でも精度を保証することを目指す ThickNumber タイプの外向きの丸めを考慮しています。
