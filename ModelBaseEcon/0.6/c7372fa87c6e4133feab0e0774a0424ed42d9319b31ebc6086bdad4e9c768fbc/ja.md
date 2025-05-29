```
inverse_transformation(::Type{<:Transformation})
```

シミュレーションデータを解決した後に変換するために呼び出される `Function` を返します。詳細は [`transformation`](@ref) を参照してください。

`transformation(T) ∘ inverse_transformation(T) == identity` および `inverse_transformation(T) ∘ transformation(T) == identity` が期待されますが、これらは検証されていません。
