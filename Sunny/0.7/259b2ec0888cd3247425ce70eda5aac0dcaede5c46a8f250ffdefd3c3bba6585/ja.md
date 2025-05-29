```
ImplicitMidpoint(dt::Float64; atol=1e-12) where N
```

ランドー・リフシッツスピンダイナミクスのための暗黙的中点法、またはSU(*N*)コヒーレント状態への一般化 [1]。[`step!`](@ref) 関数を1回呼び出すことで、[`System`](@ref) を `dt` 単位の時間だけ進めることができます。この積分スキームは完全にシンプレクティックであり、任意の長さのシミュレーショントラジェクトリにわたってエネルギードリフトを排除します。

## 参考文献

1. [H. Zhang and C. D. Batista, *Classical spin dynamics based on SU(N) coherent states*, Phys. Rev. B **104**, 104409 (2021)](https://doi.org/10.1103/PhysRevB.104.104409).
