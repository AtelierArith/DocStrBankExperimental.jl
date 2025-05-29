ブートストラップ結果をプロットします。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。
  * xs: ブートストラップ値の配列。

# オプションの引数

  * ci: 論理値、信頼区間をプロットする場合はtrue。
  * cilev: 信頼区間のレベル。
  * saving: 論理値、出力を保存する必要がある場合はtrue。
  * plotarg: プロットのための他の入力。
