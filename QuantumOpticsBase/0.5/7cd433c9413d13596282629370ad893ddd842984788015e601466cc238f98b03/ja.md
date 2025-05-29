```
ChargeBasis(ncut) <: Basis
```

`-ncut, ..., ncut` の電荷状態を span する Basis で、これは連続 U(1) 自由度のフーリエモード（不可約表現）であり、`ncut` で切り捨てられます。

電荷基底は、ハミルトニアンが次の形を持つ「トランスモン」のような回路-QED 要素にとって自然な表現です。

```julia
b = ChargeBasis(ncut)
H = 4E_C * (n_g * identityoperator(b) + chargeop(b))^2 - E_J * cosφ(b)
```

エネルギーは電荷オフセット `n_g` に周期的です。詳細は e.g. https://arxiv.org/abs/2005.12667 を参照してください。
