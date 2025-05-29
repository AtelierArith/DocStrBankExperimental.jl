最適化関数を最小化点の周りでプロットします。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメント[`EstimationSetup`](@ref)を参照してください。
  * mmsolu: EstimationResultのインスタンス。別のドキュメント[`EstimationResult`](@ref)を参照してください。
  * margobj: 最小化点の周りの目的関数値を含む配列。

# オプションの引数

  * glob: 論理値、グローバルステージのみが実行された場合はtrue。
  * plotarg: プロットのための他の入力。
