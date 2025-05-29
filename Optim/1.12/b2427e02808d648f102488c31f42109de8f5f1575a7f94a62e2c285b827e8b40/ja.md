# O-ACCEL

## コンストラクタ

```julia
OACCEL(;manifold::Manifold = Flat(),
       alphaguess = LineSearches.InitialStatic(),
       linesearch = LineSearches.HagerZhang(),
       nlprecon = GradientDescent(
           alphaguess = LineSearches.InitialStatic(alpha=1e-4,scaled=true),
           linesearch = LineSearches.Static(),
           manifold = manifold),
       nlpreconopts = Options(iterations = 1, allow_f_increases = true),
       ϵ0 = 1e-12,
       wmax::Int = 10)
```

## 説明

このアルゴリズムは、非線形前処理器 `nlprecon` によって与えられたステップを取り、前の `wmax` 回の反復によって張られた部分空間で目的関数の近似を最小化することによって加速されたステップを提案します。

O-ACCEL は N-GMRES のわずかな調整であり、最初に [1] で提示されました。

## 参考文献

[1] Riseth. Objective acceleration for unconstrained optimization. 2018.
