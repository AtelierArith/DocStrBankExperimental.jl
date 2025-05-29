```julia
is_subset_basis(basis1, basis2)

```

`basis1`の係数が[`augment_coefficients`](@ref)を使って`basis2`に拡張できるかどうかを示す`Bool`を返します。

!!! note
    `true`は、`basis1`の係数が単にゼロでパディングできることを意味するわけではありません。なぜなら、それらは異なる位置にある可能性があるからです。必ず[`augment_coefficients`](@ref)を使用してください。

