```
map_coefficients_to!(output::AbstractPolynomialLike, f::Function, p::AbstractPolynomialLike, nonzero = false)
```

`output`を変異させ、`p`の各係数`α`を`f(α)`で置き換えます。関数がゼロを返す場合、その項は削除されます。関数が非ゼロの入力に対してゼロを返さないことが知られている場合、`nonzero`を`true`に設定することでわずかな速度向上が得られます。関数は`output`を返し、これは最初の引数と同一です。

[`map_coefficients!`](@ref)および[`map_coefficients`](@ref)も参照してください。
