```
SimData(name = "my_simulation", phases::Vector{Phases} = [phase1, phase2...])
```

`runTMS`で使用するシミュレーションを記述するための型

# フィールド

  * `name`:            結果を保存するディレクトリの名前として使用されるシミュレーションの名前
  * `phases`:          シミュレーションのフェーズのリスト（可能な値のリストについてはPhasesを参照）
  * `descritpion`:     シミュレーションの説明ファイルに記載されるテキスト（デフォルトは""）
  * `time_start`:      初期シミュレーション時間（デフォルトは0.）
  * `final_measures`:  シミュレーションの終了時に行う測定（デフォルトは[]）`measure`および`output`を参照
  * `time_format`:     シミュレーション時間の出力用のC風フォーマット（デフォルトは"%8.4g"）
  * `data_format`:     シミュレーションデータの出力用のC風フォーマット（デフォルトは"%12.6g"）
