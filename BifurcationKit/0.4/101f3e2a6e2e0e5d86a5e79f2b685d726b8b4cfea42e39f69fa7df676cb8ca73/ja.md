```julia
continuation_hopf(
    prob_vf,
    alg,
    hopfpointguess,
    par,
    lens1,
    lens2,
    eigenvec,
    eigenvec_ad,
    options_cont;
    update_minaug_every_step,
    normC,
    linsolve_adjoint,
    bdlinsolver,
    bdlinsolver_adjoint,
    jacobian_ma,
    compute_eigen_elements,
    usehessian,
    kind,
    massmatrix,
    record_from_solution,
    kwargs...
)

```

コディム2のホップ点の連続性。この関数は、ホップ点の初期推測を最小限の拡張形式に基づいてホップ点の曲線に変換します。引数は次のとおりです。

  * `prob::AbstractBifurcationProblem`
  * `hopfpointguess` ホップ点の初期推測 (x*0, p1*0)。`Vector` または `BorderedArray` である必要があります。
  * `par` パラメータのセット
  * `lens1` パラメータ1のパラメータ軸
  * `lens2` パラメータ2のパラメータ軸
  * `eigenvec` p1_0 における iω の固有ベクトルの推測
  * `eigenvec_ad` p1_0 における -iω の固有ベクトルの推測
  * `options_cont` 通常の [`continuation`](@ref) に渡されるキーワード引数

# オプション引数:

  * `jacobian_ma::Symbol = :autodiff` フォールド問題の線形システムがどのように解かれるか。`:autodiff, :finiteDifferencesMF, :finiteDifferences, :minaug` のいずれか。
  * `linsolve_adjoint` (J+iω)^* ⋅sol = rhs のためのソルバー
  * `bdlinsolver` 制約方程式のためのボーダー付き線形ソルバーで、左上ブロックは (J-iω)。最小限の拡張ホップ関数の線形ソルバーで必要です。このオプションは、特定の前処理器を持つ専用の線形ソルバーを渡すために使用できます。
  * `bdlinsolver_adjoint` 制約方程式のためのボーダー付き線形ソルバーで、左上ブロックは (J-iω)^*。最小限の拡張ホップ関数の線形ソルバーで必要です。このオプションは、特定の前処理器を持つ専用の線形ソルバーを渡すために使用できます。
  * `update_minaug_every_step` 最小限の形式で `update_minaug_every_step` ステップごとにベクトル `a,b` を更新
  * `compute_eigen_elements = false` 固有要素を計算するかどうか。`options_cont.detect_event>0` の場合、ZH、HH点の検出を可能にします。
  * `kwargs` 通常の [`continuation`](@ref) に渡されるキーワード引数

# 簡略化された呼び出し:

```
continuation_hopf(br::AbstractBranchResult, ind_hopf::Int, lens2::AllOpticTypes, options_cont::ContinuationPar ;  kwargs...)
```

ここで、パラメータは上記と同様ですが、`continuation` の呼び出しの結果からブランチ `br` を渡す必要があり、`index` は `br` 内のホップ点のインデックスで、洗練したいものです。

!!! tip "ODE問題"
    ODE問題の場合、オプション `bdlinsolver = MatrixBLS()` を渡すことで、行列ベースのボーダー付き線形ソルバーを使用する方が効率的です。これがデフォルト設定です。


!!! tip "ヤコビ行列の転置"
    ヤコビ行列 `J` の随伴は、`Jᵗ = nothing` の場合に内部で計算され、`transpose(J)` を使用します。これは `J` が `AbstractArray` の場合にうまく機能します。この場合、`Jᵗ = (x, p) -> transpose(d_xF(x, p))` のようにヤコビ行列の随伴を渡さないでください。そうしないと、ヤコビ行列が2回計算されてしまいます！


!!! tip "ボグダノフ-タケンスおよびバウティン分岐の検出"
    検出をトリガーするには、`options_cont` に `detect_event = 1,2` を渡してください。`prob` に `d3F` を提供する必要があることに注意してください。

