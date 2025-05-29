```julia
tableest(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult;
    glob,
    saving,
    filename_suffix
)

```

パラメータ推定を含むDataFrameを作成し、オプションで保存します。

# 必須引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。

# オプション引数

  * glob: 論理値、グローバルステージのみが実行された場合はtrue。
  * saving: 論理値、出力を保存する必要がある場合はtrue。
