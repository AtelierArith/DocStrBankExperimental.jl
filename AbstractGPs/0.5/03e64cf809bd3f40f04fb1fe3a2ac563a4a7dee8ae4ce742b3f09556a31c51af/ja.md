```
VFE(fz::FiniteGP)
```

"変分自由エネルギー"のスパース近似[1]は、誘導入力`fz.x`を用いて近似事後分布を構築するために使用されます。使用例については[`posterior(v::VFE, fx::FiniteGP, y::AbstractVector{<:Real})`](@ref)を参照してください。

[1] - M. K. Titsias. "スパースガウス過程における誘導変数の変分学習". In: Proceedings of the Twelfth International Conference on Artificial Intelligence and Statistics. 2009.
