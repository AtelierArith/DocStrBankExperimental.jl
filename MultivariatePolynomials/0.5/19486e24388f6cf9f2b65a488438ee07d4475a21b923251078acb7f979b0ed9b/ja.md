```
halfdegree(t::AbstractTermLike)
```

実数値の項に対しては`ceil(degree(t)/2)`を、複素変数のみを含む項に対しては`degree_complex(t)`を返します。ただし、複素変数と実数値変数の混合を尊重します。定義が明確であるためには、単項式は変数の実部や虚部を含んではいけません。`x₁`と`x₂`が実数値変数で、`z₁`と`z₂`が複素数値の場合、

  * `halfdegree(x₁^2 * x₂^3) = ⌈5/2⌉ = 3`
  * `halfdegree(z₁^3 * conj(z₁)^4) = max(3, 4) = 4` および `halfdegree(z₁^4 * conj(z₁)^3) = max(4, 3) = 4`
  * `halfdegree(z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = max(4, 6) = 6` および `halfdegree(z₁^4 * z₂ * conj(z₁) * conj(z₂)^3) = max(5, 4) = 5`
  * `halfdegree(x₁^2 * x₂^3 * z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = ⌈5/2⌉ + max(4, 6) = 9`

```
