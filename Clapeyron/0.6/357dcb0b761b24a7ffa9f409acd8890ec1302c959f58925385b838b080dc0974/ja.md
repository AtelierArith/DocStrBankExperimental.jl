```
推定
Estimation(model,toestimate,filepaths,ignorefield,objective_form)
```

## 入力パラメータ:

  * `model`: パラメータ化したい種を含む初期モデル
  * `toestimate`: フィッティングされるパラメータの辞書
  * `filepaths` または `filepaths_weights`: フィッティングに使用されるデータファイルの場所。各データセットの重みも含むことができる
  * `ignorefield`: メインモデルで無視するEoSModelフィールドを指定
  * `objective_form`: 目的関数の機能的形式を `objective_form(pred,exp)` の形で指定

## 出力:

以下を含むEstimatorオブジェクト:

  * `model`: パラメータが変化するモデル
  * `initial_model`: パラメータ化前の初期モデル
  * `toestimate`: パラメータに関するすべての情報を含むToEstimate構造体
  * `data`: データに関するすべての情報が保存されている `EstimationData` 構造体のベクター
  * `ignorefield`: パラメータ推定で無視するフィールドのベクター
  * `objective_form`: 目的関数の誤差測定を評価するための関数

以下のオブジェクトも出力される:

  * `objective`: パラメータをフィットするために使用される目的関数
  * `x0`: パラメータの初期推測
  * `upper`: パラメータの上限
  * `lower`: パラメータの下限

## 説明

パラメータ推定内で使用される推定器およびその他の有用なオブジェクトを生成します
