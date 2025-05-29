```julia
continuation(
    br,
    ind_bif,
    _contParams;
    alg,
    δp,
    ampfactor,
    usedeflation,
    linear_algo,
    detailed,
    prm,
    use_normal_form,
    autodiff_nf,
    kwargs...
)

```

周期軌道 (PO) の分岐点でのブランチスイッチングは、`br::AbstractBranchResult` によって指定されます。PO を計算するための関数は `br.prob` です。分岐スイッチング機能を改善するために、デフレートニュートン-クリロフソルバーを使用できます。

!!! note "ディープコピー"
    変異を防ぐために、基礎となる周期軌道関数をディープコピーします。


# 引数

  * `br` [`PeriodicOrbitTrapProblem`](@ref) で計算された周期軌道のブランチ
  * `ind_bif` ブランチポイントのインデックス
  * `_contParams` 継続パラメータ、[`continuation`](@ref) を参照

# オプション引数

  * `δp = _contParams.ds` ブランチ内のパラメータに対する特定の推測を指定するために使用され、これは `contParams.ds` によって決定されます。これにより、`contParams.dsmax` よりも大きなステップを使用できます。
  * `ampfactor = 1` 分岐した解の振幅を変更する因子。分岐したブランチが非常に急な場合に、分岐した解を拡大するのに役立ちます。
  * `usedeflation = true` 分岐したブランチ上の推測を見つけるのを助けるために非線形デフレーションを使用するかどうか（[Deflated problems](@ref) を参照）

## 正規形の場合

  * `detailed = false` 正規形を完全に計算するかどうか。
  * `record_from_solution = (u, p) -> u[end]` 分岐図で使用される記録メソッド、デフォルトでは周期軌道の周期を記録します。
  * `autodiff_nf = true` `get_normal_form` で `autodiff` を使用するかどうか。自動微分が意図した通りに機能しない場合に使用できます。

## 継続の場合

  * `linear_algo = BorderingBLS()` [`continuation`](@ref) と同じ
  * `kwargs` 通常の [`continuation`](@ref) への呼び出しに使用されるキーワード引数と周期軌道 (PO) に特有のもの。
