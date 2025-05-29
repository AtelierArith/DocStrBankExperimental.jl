`augment_coefficients(basis1, basis2, θ1)`

`basis2`の係数`θ2`のセットを返します。これにより、

```julia
linear_combination(basis1, θ1, x) == linear_combination(basis2, θ2, x)
```

がドメイン内の任意の`x`に対して成り立ちます。実際には、ゼロでパディングすることを意味します。

基底が互換性がない場合や`x`との互換性がない場合、またはこれが不可能な場合は`ArgumentError`をスローします。互換性のない基底に対してメソッドは定義されていない場合があり、基底間の互換性は[`is_subset_basis`](@ref)で確認できます。
