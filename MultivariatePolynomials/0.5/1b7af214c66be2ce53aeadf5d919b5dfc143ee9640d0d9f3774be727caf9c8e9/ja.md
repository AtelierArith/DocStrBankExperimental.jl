```
map_coefficients_to!(output::AbstractPolynomialLike, f::Function, p::AbstractPolynomialLike, nonzero = false)
```

`p`の各係数`α`を`f(α)`で置き換えることによって`output`を変更します。関数がゼロを返す場合、その項は削除されます。関数が非ゼロの入力に対してゼロを返さないことが知られている場合、`nonzero`を`true`に設定することでわずかな速度向上が得られます。この関数は、最初の引数と同一の`output`を返します。

[`map_coefficients!`](@ref)および[`map_coefficients`](@ref)も参照してください。
