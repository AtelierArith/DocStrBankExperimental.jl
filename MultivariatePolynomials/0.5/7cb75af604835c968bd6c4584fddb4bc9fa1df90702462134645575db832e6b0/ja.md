```
degree_complex(t::AbstractTermLike)
```

項 `t` の単項式の *全複素次数* を返します。すなわち、`t` における宣言された変数の全次数と、`t` における共役変数の全次数の最大値です。定義が明確であるためには、単項式は変数の実部や虚部を含んではいけません。もし `x₁` と `x₂` が実数値の変数で、`z₁` と `z₂` が複素数値の変数であるとき、

  * `degree_complex(x₁^2 * x₂^3) = 5`
  * `degree_complex(z₁^3 * conj(z₁)^4) = max(3, 4) = 4` および `degree_complex(z₁^4 * conj(z₁)^3) = max(4, 3) = 4`
  * `degree_complex(z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = max(4, 6) = 6` および `degree_complex(z₁^4 * z₂ * conj(z₁) * conj(z₂)^3) = max(5, 4) = 5`
  * `degree_complex(x₁^2 * x₂^3 * z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = 5 + max(4, 6) = 11`

```
