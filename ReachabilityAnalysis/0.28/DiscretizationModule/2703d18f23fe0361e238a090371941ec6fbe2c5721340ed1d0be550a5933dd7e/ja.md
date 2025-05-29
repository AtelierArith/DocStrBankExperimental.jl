```
discretize(ivp::IVP, δ, alg::AbstractApproximationModel)
```

連続時間初期値問題を離散時間問題に保守的に離散化するための集合ベースの手法です。

### 入力

  * `ivp`   – 標準形の線形ODEに対する初期値問題（以下の`Notes`を参照）
  * `δ`     – ステップサイズ
  * `alg`   – 近似モデルを計算するために使用されるアルゴリズム

### 出力

離散システムの初期値問題。

### 注意事項

異なる近似アルゴリズムとそれぞれのオプションは、各メソッドのドキュメントに記載されています。以下は、利用可能なすべての近似モデルのリストです：

```jldoctest
julia> subtypes(ReachabilityAnalysis.DiscretizationModule.AbstractApproximationModel)
9-element Vector{Any}:
 Backward
 CorrectionHull
 FirstOrder
 FirstOrderZonotope
 Forward
 ForwardBackward
 NoBloating
 SecondOrderddt
 StepIntersect
```

この関数で考慮される初期値問題は次の形です

$$
x' = Ax(t) + u(t),\qquad x(0) ∈ \mathcal{X}_0,\qquad (1)
$$

ここで、$u(t) ∈ U(k)$ は非決定的入力の集合の列 $\{U(k)\}_k$ であり、$\mathcal{X}_0$ は初期状態の集合です。他の問題、例えば $x' = Ax(t) + Bu(t)$ は、関数 [`normalize`](@ref) を使用して標準形に変換できます。

各アルゴリズムを紹介する元の論文への参照については、ドキュメントを参照してください。例えば、`?Forward`。
