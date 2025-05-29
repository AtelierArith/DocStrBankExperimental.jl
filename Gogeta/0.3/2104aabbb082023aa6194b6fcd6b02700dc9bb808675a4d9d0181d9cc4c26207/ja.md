```
function create_MIP_from_CNN!(jump_model::JuMP.Model, CNN_model::Flux.Chain, cnnstruct::CNNStructure)
```

`Flux.Chain` 畳み込みニューラルネットワークモデルから混合整数最適化問題を作成します。最適化の定式化は、入力として与えられた `JuMP.Model` に保存されます。

ダミーの目的関数として 1 がモデルに追加されます。目的はユーザーが定義することになっています。

畳み込みニューラルネットワークは特定の構造に従う必要があります：

  * 畳み込み層とプーリング層、`Flux.flatten` 層、そして最後に密な層から構成される必要があります
  * すなわち、許可される層のタイプ：`Conv`、`MaxPool`、`MeanPool`、`Flux.flatten`、`Dense`
  * すべての畳み込み層と密な層の活性化関数は `ReLU` でなければなりません
  * 最後の密な層は `identity` 活性化関数を使用しなければなりません
  * 入力サイズ、フィルターサイズ、ストライド、パディングは自由に選択できます

# パラメータ

  * `jump_model`: 定式化が保存される空の最適化モデル
  * `CNN_model`: CNN を含む `Flux.Chain`
  * `cnnstruct`: CNN の層構造を保持します

# オプションのパラメータ

  * `max_to_mean`: maxpool 層を meanpool 層として定式化します。これにより、リラクゼーションウォークアルゴリズムで使用するためのモデルの凸包（線形緩和）が改善される可能性があります。
  * `logging`: 進捗情報をコンソールに出力します。
