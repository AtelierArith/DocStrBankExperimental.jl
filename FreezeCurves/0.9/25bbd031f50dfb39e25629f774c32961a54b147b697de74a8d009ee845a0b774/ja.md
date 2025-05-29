```
SFCCInverseEnthalpyObjective{TF,Tkwargs<:NamedTuple,Thc,TL,TH,Tsat} <: AbstractSFCCObjective
```

温度 `T` を求めるための最適化目的で、保存方程式を解決します：

$$
0 = (H - Lθ)/C - T
$$

固定されたエンタルピー値 `H` と凍結曲線引数 `f_args` が与えられます。
