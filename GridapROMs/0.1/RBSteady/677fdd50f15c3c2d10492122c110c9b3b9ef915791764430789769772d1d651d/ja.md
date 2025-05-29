```
struct RBSolver{A<:GridapType,B} <: GridapType
  fesolver::A
  state_reduction::Reduction
  residual_reduction::Reduction
  jacobian_reduction::B
end
```

FEソルバー（例：[`Gridap`](@ref)の`NonlinearSolver`または`ODESolver`）のラッパーで、与えられた問題を解決するために使用される縮約基底（RB）法に関する追加情報を持っています。RB法は、次のような射影ベースの縮約オーダーモデルです。

1. 次元n << NₕのFESpaceの適切な部分空間を探します。
2. 行列ベースの離散経験的補間法（MDEIM）が実行されます。

パラメトリック残差とヤコビアンの多様体を近似するために、

3. EIM近似は（ペトロフ）ガレルキン射影を用いて部分空間に圧縮されます。
4. 各パラメータの選択に対して、数値積分が実行され、

結果として得られるn × nの方程式系が安価に解かれます。

特に：

  * tol: 射影ベースの切断適正直交分解（TPOD）またはテンソルトレイン特異値分解（TT-SVD）で使用される許容誤差。ここでは、縮約部分空間を生成する基底が計算されます。tolの値は部分空間の次元を選択する役割を果たします。すなわち、n = n(tol)です。
  * nparams_state: TPODまたはTT-SVDを実行する際に考慮されるスナップショットの数
  * nparams_res: 残差のためにMDEIMを実行する際に考慮されるスナップショットの数
  * nparams_jac: ヤコビアンのためにMDEIMを実行する際に考慮されるスナップショットの数
  * nparams_test: RB法がFE手続きに対して犯す誤差を計算する際に考慮されるスナップショットの数
