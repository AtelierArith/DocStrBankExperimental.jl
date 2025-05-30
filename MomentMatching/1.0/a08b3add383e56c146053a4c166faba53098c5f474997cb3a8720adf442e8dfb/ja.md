最適化関数を最小化点の周りでプロットします。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。
  * margobj: 最小化点の周りの目的関数値を含む配列。

# オプションの引数

  * glob: 論理値、グローバルステージのみが実行された場合はtrue。
  * plotarg: プロットのための他の入力。
