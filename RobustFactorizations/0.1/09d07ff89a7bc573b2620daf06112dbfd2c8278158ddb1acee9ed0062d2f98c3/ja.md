```
RPCA = rpca(A::Matrix; λ=1.0 / √(maximum(size(A))), iters=1000, tol=1.0e-7, ρ=1.5, verbose=false, nonnegL=false, nonnegS=false, nukeA=true)
```

minimize*{L,D,S} ||L||** + λ||S||₁ + γ||D||₂² s.t. A = L+D+S

Ref: "The Augmented Lagrange Multiplier Method for Exact Recovery of Corrupted Low-Rank Matrices", Zhouchen Lin, Minming Chen, Leqin Wu, Yi Ma, https://people.eecs.berkeley.edu/~yima/psfile/Lin09-MP.pdf

#Arguments:

  * `A`: 入力行列
  * `λ`: スパース性正則化
  * `iters`: 最大反復回数
  * `tol`: 許容誤差
  * `ρ`: アルゴリズム調整パラメータ
  * `verbose`: ステータスを表示
  * `nonnegL`: Aに対するハードしきい値処理
  * `nonnegS`: Eに対するハードしきい値処理
  * `proxL`: NuclearNorm(1/2)
  * `proxD`: なし
  * `proxS`: NormL1(λ))

収束を速めるためには、許容誤差を増やすか、`ρ`を増やすことができます。`tol`を増やすことがしばしば最良の解決策です。
