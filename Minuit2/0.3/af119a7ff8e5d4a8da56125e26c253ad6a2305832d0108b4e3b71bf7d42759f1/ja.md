```
minos!(m::Minuit, name::String)
```

Minosアルゴリズムを実行して、単一のパラメータの非対称誤差を計算します。

Minosアルゴリズムは、プロファイル尤度法を使用して（一般的に非対称の）信頼区間を計算します。最小値の周りで負の対数尤度または（同等に）最小二乗コスト関数をスキャンして、信頼区間を構築します。

## 引数

  * `m::Minuit` : 最小化するMinuitオブジェクト。
  * `parameters::AbstractVector{String}` : Minos誤差を計算するためのパラメータの名前。
  * `cl::Number` : 区間の信頼レベル。設定されていない場合、標準の68%の区間が計算されます（デフォルト）。0 < cl < 1の場合、その値は信頼レベル（確率）として解釈されます。便宜上、cl >= 1の値は、その数の標準偏差をカバーする中心対称区間の確率内容として解釈されます。たとえば、cl=1は68.3%として解釈され、cl=2は84.3%として解釈されます。0.68、0.9、0.95、0.99、1、2、3、4、5以外の値を使用するには、scipyモジュールが必要です。
  * `ncall::Int` : Minosによって行われる呼び出しの数を制限します。0の場合、Minuit2ライブラリの適応的内部ヒューリスティックが使用されます（デフォルト：0）。

## 注意事項

漸近的に（大きなサンプルの場合）、Minos区間は与えられた信頼レベルと等しいカバレッジ確率を持ちます。カバレッジ確率は、区間が繰り返し同一の実験で真の値を含む確率です。

区間は変換に対して不変であり、したがって信頼区間と交差しない限り、パラメータの制限によって歪められることはありません。一般的なルールとして、HesseアルゴリズムとMinosアルゴリズムで計算された信頼区間が大きく異なる場合、Minos区間が好まれます。そうでない場合は、Hesse区間が好まれます。

多くのフィットパラメータがある場合、Minosを実行することは計算コストが高くなります。実際には、1つのパラメータを小さなステップでスキャンし、各スキャンポイントのコスト関数の他のすべてのパラメータに対して完全な最小化を実行します。これには、Hesseアルゴリズムを実行するよりも多くの関数評価が必要です。
