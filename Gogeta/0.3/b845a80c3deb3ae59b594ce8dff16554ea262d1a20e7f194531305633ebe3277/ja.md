```
function ICNN_incorporate!(jump::JuMP.Model, filepath::String, output_var, input_vars...)
```

入力凸ニューラルネットワーク（ICNN）をLPとしてJuMPモデルに組み込みます。モデルパラメータは、指定されたファイルパスにあるJSONファイルに含まれている必要があります。ICNNに関する詳細は、Amos et al. (2017)を参照してください。

JSONファイルの構造：

  * パラメータセットは、レイヤータイプに基づいて名前を付ける必要があります - "FCx"または"SKIPx"のいずれかで、'x'はレイヤー番号を示します。
  * 'FC'は全結合層を示します。これらのパラメータセットには重みとバイアスが含まれています。
  * 'SKIP'はスキップ接続層を示します。これらには重みのみが含まれています。
  * Tensorflowからこれらのパラメータをエクスポートする方法の明確な例については、パッケージリポジトリのexamples/-フォルダを参照してください。

この関数は、入力として与えられたJuMPモデルを修正します。この関数に入力として与えられた入力および出力変数の参照は、ICNNの定式化における適切な変数にリンクされます。JuMPモデルには追加の名前は付けられず、すべての変数は匿名として追加されます。また、JuMPモデルの目的関数は、ICNN出力をペナルティ項として含むように修正されます。

# 引数

  * `jump`: LP定式化が組み込まれるJuMPモデル
  * `filepath`: モデルパラメータを含むJSONファイルへの相対パス
  * `output_var`: ICNN出力にリンクされるべき変数への参照
  * `input_vars`: ICNN入力として使用される変数への参照

```
