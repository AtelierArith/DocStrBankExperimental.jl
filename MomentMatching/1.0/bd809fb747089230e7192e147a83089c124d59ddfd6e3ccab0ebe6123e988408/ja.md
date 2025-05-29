すべての試行における推定パラメータの系列をプロットします。

解が最小化器の周りで安定している場合、これは安定性を示します。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。

# オプションの引数

  * glob: 論理値、グローバルステージのみが実行された場合はtrue。
  * firstN: プロットする観測値の数。
