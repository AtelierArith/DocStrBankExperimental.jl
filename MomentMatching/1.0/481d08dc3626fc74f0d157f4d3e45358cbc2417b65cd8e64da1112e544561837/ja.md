```julia
tableest(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    boot::MomentMatching.BootstrapResult;
    cilev,
    dgt,
    glob,
    saving,
    filename_suffix
)

```

パラメータ推定値を含むDataFrameを作成し、オプションで保存します。ブートストラップケース。

# 必須引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。
  * boot: BootstrapResultのインスタンス。別のドキュメントを参照してください [`BootstrapResult`](@ref)。

# オプション引数

  * cilev: 信頼区間のレベル。
  * glob: 論理値、グローバルステージのみが実行された場合はtrue。
  * saving: 論理値、出力を保存する必要がある場合はtrue。
