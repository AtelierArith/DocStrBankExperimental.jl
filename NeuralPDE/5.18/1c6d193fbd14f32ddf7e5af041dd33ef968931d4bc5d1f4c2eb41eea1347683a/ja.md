```
ahmc_bayesian_pinn_pde(pde_system, discretization;
    draw_samples = 1000, bcstd = [0.01], l2std = [0.05], phystd = [0.05],
    phynewstd = [0.05], priorsNNw = (0.0, 2.0), param = [], nchains = 1,
    Kernel = HMC(0.1, 30), Adaptorkwargs = (Adaptor = StanHMCAdaptor,
        Metric = DiagEuclideanMetric, targetacceptancerate = 0.8),
    Integratorkwargs = (Integrator = Leapfrog,), saveats = [1 / 10.0],
    numensemble = floor(Int, draw_samples / 3), progress = false, verbose = false)
```

## 注意事項

  * データセットは、正確なパラメータ推定と方程式の解決に必要です。
  * 返される解は、選択した `saveats` グリッド間隔とチェーン内の最後の n = `numensemble` サンプルに対するアンサンブル解、推定された PDE および NN パラメータで構成される BPINNsolution です。MCMC チェーン内のサンプルの完全なセットは `fullsolution` として返されます。詳細については `BPINNsolution` を参照してください。

## 位置引数

  * `pde_system`: ModelingToolkit で定義された PDE 方程式または方程式のシステム。
  * `discretization`: 与えられた pde_system に対する BayesianPINN の離散化、ニューラルネットワークおよびトレーニング戦略。

## キーワード引数

  * `draw_samples`: MCMC アルゴリズムで引き出すサンプルの数（ウォームアップサンプルは引き出しサンプルの約 2/3）。
  * `bcstd`: 初期/境界条件方程式に対する BPINN 予測の標準偏差のベクトル。
  * `l2std`: 各依存変数に対する BPINN 予測の L2 損失/データセットの標準偏差のベクトル。
  * `phystd`: 選択した基礎 PDE 方程式に対する BPINN 予測の標準偏差のベクトル。
  * `phynewstd`: 新しい損失項の標準偏差のベクトル。
  * `priorsNNw`: BPINN ネットワークパラメータの (平均、標準偏差) のタプル。BPINN の重みとバイアスはデフォルトで正規分布です。
  * `param`: 逆問題の場合の選択した PDE のパラメータの分布のベクトル。
  * `nchains`: サンプリングしたいチェーンの数。
  * `Kernel`: MCMC サンプリングアルゴリズムオブジェクト HMC/NUTS/HMCDA の選択 (AdvancedHMC.jl の実装)。
  * `Adaptorkwargs`: `Adaptor`、`Metric`、`targetacceptancerate`。参照: https://turinglang.org/AdvancedHMC.jl/stable/。注意: 提案が受け入れられるイテレーションのターゲットパーセンテージ（小数で、デフォルトは 0.8）。
  * `Integratorkwargs`: `Integrator`、`jitter_rate`、`tempering_rate`。参照: https://turinglang.org/AdvancedHMC.jl/stable/
  * `saveats`: アンサンブル解、推定パラメータの評価のための各独立変数のグリッド間隔。
  * `numensemble`: アンサンブル解、推定パラメータの作成のために取る最後のサンプルの数。
  * `progress`: 進捗メーターを表示するかどうかを制御します。
  * `verbose`: 詳細度を制御します。（AHMC でのサンプル呼び出し引数）。

!!! 警告     AdvancedHMC.jl はまだ便利な構造体を開発中であり、新しいリリースで変更が必要になる可能性があります。
