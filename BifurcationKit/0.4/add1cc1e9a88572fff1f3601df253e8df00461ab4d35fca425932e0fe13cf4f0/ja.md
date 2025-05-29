```julia
continuation(
    br,
    ind_bif,
    _contParams,
    pbPO;
    bif_prob,
    alg,
    δp,
    ampfactor,
    usedeflation,
    detailed,
    use_normal_form,
    autodiff_nf,
    nev,
    kwargs...
)

```

自動分岐スイッチングを、以前に計算された分岐 `br::ContResult` の分岐点のリストにラベル付けされた `ind_bif` のホップ分岐点から実行します。最初にホップ正規形を計算します。

# 引数

  * `br` `continuation` の呼び出しからの分岐結果
  * `ind_hopf` `br` における分岐点のインデックス
  * `contParams` `continuation` の呼び出しに対するパラメータ
  * `probPO` 周期軌道を計算する方法を指定するために使用される問題。 [`PeriodicOrbitTrapProblem`](@ref)、[`PeriodicOrbitOCollProblem`](@ref)、[`ShootingProblem`](@ref) または [`PoincareShootingProblem`](@ref) のいずれかです。

# オプション引数

  * `alg = br.alg` 継続アルゴリズム
  * `δp` 分岐した分岐のパラメータの推測を指定するために使用され、デフォルトでは `contParams.ds` になります。これにより、初期ステップを `contParams.dsmax` より大きくすることができます。
  * `ampfactor = 1` 分岐した解の振幅を変更するための乗数因子。分岐した分岐が非常に急な場合に、分岐した解を拡大するのに便利です。
  * `use_normal_form = true` 予測子を計算するために正規形を使用するかどうか。 `false` の場合、`ampfactor` と `δp` が分岐する固有ベクトルに基づいて予測子を作成するために使用されます。例えば、高次の導関数が利用できない場合など、正規形を計算することが不可能な場合には、`use_normal_form = false` を設定することが有用です。
  * `usedeflation = true` 分岐した分岐の推測を見つけるのを助けるために非線形デフレーションを使用するかどうか（[Deflated problems](@ref)を参照）
  * `nev` 正しい固有ベクトルを得るために計算される固有値の数
  * `autodiff_nf = true` `get_normal_form` で `autodiff` を使用するかどうか。自動微分が意図した通りに機能していない場合に使用できます。
  * [`continuation`](@ref) からのすべての `kwargs`

修正されたバージョンの `prob` が `plot_solution` と `finalise_solution` に渡されます。

!!! note "線形ソルバー"
    `contParams.newton_options.linsolver` のオプションには注意が必要です。行列フリーソルバーの場合、未知数の正しい数 `N * M + 1` を渡す必要があります。前処理器のオプションにはまだアクセスできないことに注意してください。

