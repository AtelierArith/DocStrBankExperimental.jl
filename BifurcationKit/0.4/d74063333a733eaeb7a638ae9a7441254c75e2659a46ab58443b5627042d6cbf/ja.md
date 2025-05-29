```julia
mutable struct FoldProblemMinimallyAugmented{Tprob<:BifurcationKit.AbstractBifurcationProblem, vectype, T<:Real, S<:BifurcationKit.AbstractLinearSolver, Sa<:BifurcationKit.AbstractLinearSolver, Sbd<:BifurcationKit.AbstractBorderedLinearSolver, Sbda<:BifurcationKit.AbstractBorderedLinearSolver, Tmass, Tn} <: BifurcationKit.AbstractProblemMinimallyAugmented{Tprob<:BifurcationKit.AbstractBifurcationProblem}
```

最小拡張形式に基づくFold / Hopf関数をエンコードするための構造体。

# フィールド

  * `prob_vf`: 関数 F(x, p) - ベクトル場 - すべての導関数を含む。
  * `a`: Jᵗの零ベクトルに近い。
  * `b`: Jの零ベクトルに近い。
  * `zero`: 多くの回数割り当てを避けるためのゼロベクトル。
  * `l1`: リャプノフ係数。
  * `CP`: カスプテスト値。
  * `BT`: ボグダノフ-タケンステスト値。
  * `GH`: バウティンテスト値。
  * `ZH`: ゼロ-ホップテスト値。
  * `linsolver`: 線形ソルバー。MA関数のヤコビアンを反転するために使用される。
  * `linsolverAdjoint`: ヤコビアン随伴のための線形ソルバー。
  * `linbdsolver`: 境界付き線形ソルバー。
  * `linbdsolverAdjoint`: ヤコビアン随伴のための線形境界付きソルバー。
  * `usehessian`: prob_vfのヘッセ行列を使用するかどうか。
  * `massmatrix`: M⋅∂ₜu = F(u)を研究するための質量行列Mを使用するかどうか、デフォルトはI。
  * `norm`: 更新またはテストでベクトルを正規化するためのノルム。
  * `update_minaug_every_step`: 各ステップごとに問題を更新する。
