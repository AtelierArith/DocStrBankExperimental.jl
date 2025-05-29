```
Hybrid{P} <: AbstractAlgorithm{P}
```

パウエルのハイブリッド法の修正版（ドッグレッグを用いた信頼領域法）。本質的に同じアルゴリズムは、根の発見問題と最小二乗問題の両方を解決できます。問題のタイプを示すために、型パラメータとして `RootFinding` または `LeastSquares` のいずれかを設定します。このアルゴリズムを使用する際に `init` および `solve` で受け入れられるキーワード引数については、[`HybridSolver`](@ref)を参照してください。

# 参考文献

  * **Moré, Jorge J., Danny C. Sorenson, Burton S. Garbow, and Kenneth E. Hillstrom.** 1984. "The MINPACK Project." In *Sources and Development of Mathematical Software*, ed. Wayne R. Cowell, 88-111. New Jersey: Prentice-Hall.
  * **Nocedal, Jorge, and Stephen J. Wright.** 2006. *Numerical Optimization.* 2nd ed. New York: Springer.
  * **Powell, Michael J. D.** 1970. "A Hybrid Method for Nonlinear Equations." In *Numerical Methods for Nonlinear Algebraic Equations*, ed. Philip Rabinowitz, 87-114. London: Gordon and Breach.
