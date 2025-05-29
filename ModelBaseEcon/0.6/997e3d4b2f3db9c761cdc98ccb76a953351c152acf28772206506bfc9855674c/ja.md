```
transformation(::Type{<:Transformation})
```

モデル方程式に代入され、解決する前に入力データを変換するために呼び出される`Function`を返します。詳細は[`inverse_transformation`](@ref)を参照してください。

`transformation(T) ∘ inverse_transformation(T) == identity`および`inverse_transformation(T) ∘ transformation(T) == identity`が期待されますが、これらは検証されていません。
