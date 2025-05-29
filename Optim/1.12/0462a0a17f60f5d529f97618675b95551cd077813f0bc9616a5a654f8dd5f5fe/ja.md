# N-GMRES

## コンストラクタ

```julia
NGMRES(;
        alphaguess = LineSearches.InitialStatic(),
        linesearch = LineSearches.HagerZhang(),
        manifold = Flat(),
        wmax::Int = 10,
        ϵ0 = 1e-12,
        nlprecon = GradientDescent(
            alphaguess = LineSearches.InitialStatic(alpha=1e-4,scaled=true),
            linesearch = LineSearches.Static(),
            manifold = manifold),
        nlpreconopts = Options(iterations = 1, allow_f_increases = true),
      )
```

## 説明

このアルゴリズムは、非線形前処理器 `nlprecon` によって与えられたステップを取り、前の `wmax` 回の反復によって張られた部分空間での勾配の (ll_2) 残差の近似を最小化することによって加速されたステップを提案します。

N-GMRES は元々非線形システムを解くために開発され、線形問題に対しては GMRES に還元されます。最適化へのアルゴリズムの適用については、例えば [2] で取り上げられています。

## 参考文献

[1] De Sterck. Steepest descent preconditioning for nonlinear GMRES optimization. NLAA, 2013. [2] Washio and Oosterlee. Krylov subspace acceleration for nonlinear multigrid schemes. ETNA, 1997.
