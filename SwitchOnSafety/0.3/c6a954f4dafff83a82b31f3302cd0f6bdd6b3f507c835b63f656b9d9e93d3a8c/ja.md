```
soslyap(s::AbstractSwitchedSystem, d; optimizer_constructor=nothing)
```

Sum-of-Squares Lyapunov関数を見つけます。すなわち、[(5), PJ08]を解くか、問題の不可能性を証明するモーメント行列を提供します。異なる成長率を使用するには、[`ScaledHybridSystem`](@ref)を使用してください。

[PJ08] P. Parrilo and A. Jadbabaie. *合計平方を用いた共通スペクトル半径の近似*. 線形代数とその応用, Elsevier, **2008**, 428, 2385-2402
