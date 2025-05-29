```julia
continuation_fold(
    prob,
    alg,
    foldpointguess,
    par,
    lens1,
    lens2,
    eigenvec,
    eigenvec_ad,
    options_cont;
    update_minaug_every_step,
    normC,
    bdlinsolver,
    bdlinsolver_adjoint,
    jacobian_ma,
    compute_eigen_elements,
    usehessian,
    kind,
    record_from_solution,
    kwargs...
)

```

コーディン 2 続きの折れ点。この関数は、折れ点の初期推測を最小限に拡張された定式化に基づいて折れ点の曲線に変換します。引数は次のとおりです。

  * `prob::AbstractBifurcationFunction`
  * `foldpointguess` 折れ点の初期推測 (x*0, p1*0)。これは、関数 `foldpoint` によって返される `BorderedArray` である必要があります。
  * `par` パラメータのセット
  * `lens1` パラメータ 1 のパラメータ軸
  * `lens2` パラメータ 2 のパラメータ軸
  * `eigenvec` 右の零ベクトルの推測
  * `eigenvec_ad` 左の零ベクトルの推測
  * `options_cont` 通常の [`continuation`](@ref) に渡される引数

# オプションの引数:

  * `jacobian_ma::Symbol = :autodiff` 折れ点問題の線形システムがどのように解決されるか。`:autodiff, :finiteDifferencesMF, :finiteDifferences, :minaug` のいずれかにすることができます。
  * `bdlinsolver` 左上ブロック J を持つ制約方程式のための境界線形ソルバー。最小限に拡張された折れ点機能の線形ソルバーに必要です。このオプションは、特定の前処理器を持つ専用の線形ソルバーを渡すために使用できます。
  * `bdlinsolver_adjoint` 左上ブロック J^* を持つ制約方程式のための境界線形ソルバー。最小限に拡張された折れ点機能の線形ソルバーに必要です。このオプションは、特定の前処理器を持つ専用の線形ソルバーを渡すために使用できます。
  * `update_minaug_every_step` 最小限の定式化で `update_minaug_every_step` ステップごとにベクトル `a, b` を更新します。
  * `compute_eigen_elements = false` 固有要素を計算するかどうか。`options_cont.detect_event>0` の場合、ZH点の検出を可能にします。
  * `kwargs` 通常の [`continuation`](@ref) に渡されるキーワード引数

# 簡略化された呼び出し

```
continuation_fold(br::AbstractBranchResult, ind_fold::Int64, lens2::AllOpticTypes, options_cont::ContinuationPar ; kwargs...)
```

ここで、パラメータは上記の通りですが、分岐の検出が有効な `continuation` の呼び出しの結果からブランチ `br` を渡す必要があり、`index` は `br` 内の続けたい折れ点のインデックスです。

!!! tip "ヤコビ行列の転置"
    ヤコビ行列 `J` の随伴は、`Jᵗ = nothing` の場合に内部で計算され、`transpose(J)` を使用します。これは、`J` が `AbstractArray` の場合にうまく機能します。この場合、`Jᵗ = (x, p) -> transpose(d_xF(x, p))` のようにヤコビ行列の随伴を渡さないでください。そうしないと、ヤコビ行列が2回計算されます！


!!! tip "ODE問題"
    ODE問題の場合、オプション `bdlinsolver = MatrixBLS()` を渡すことで、行列ベースの境界線形ソルバーを使用する方が効率的です。これがデフォルト設定です。


!!! tip "ボグダノフ-タケンスおよびカスプ分岐の検出"
    検出をトリガーするには、`options_cont` に `detect_event = 1 or 2` を渡してください。

