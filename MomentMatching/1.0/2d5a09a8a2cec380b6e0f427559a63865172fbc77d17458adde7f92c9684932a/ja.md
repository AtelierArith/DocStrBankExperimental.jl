```julia
tablemoms(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    boot::MomentMatching.BootstrapResult;
    dgt,
    glob,
    saving,
    filename_suffix
)

```

モデル生成のモーメントをデータと比較し、テーブルに表示し、オプションで出力を保存します。ブートストラップケース。

# 必須引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。
  * boot: BootstrapResultのインスタンス。別のドキュメントを参照してください [`BootstrapResult`](@ref)。

# オプション引数

  * saving: 論理値、出力を保存する必要がある場合はtrue。
