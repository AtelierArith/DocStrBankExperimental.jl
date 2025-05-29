```
ASB07{N, AM, RM, S, R} <: AbstractContinuousPost
```

不確定なパラメータと入力を持つ線形システムの到達可能性のためのAlthoff - Stursberg - Bussアルゴリズムの実装。ゾノトープを使用しています。

## フィールド

  * `δ`                – 離散化のステップサイズ
  * `approx_model`     – (オプション、デフォルト: `CorrectionHull(; order=10, exp=:interval)`)                       近似モデル;                       可能なオプションについては下の`Notes`を参照してください
  * `max_order`        – (オプション、デフォルト: `5`) 最大ゾノトープ次数
  * `reduction_method` – (オプション、デフォルト: `GIR05()`) 使用されるゾノトープ次数削減方法
  * `static`           – (オプション、デフォルト: `false`) `true`の場合、問題データを                       静的サイズの配列に変換します
  * `recursive`        – (オプションデフォルト: `true`) `true`の場合、各到達集合を再帰的に計算する実装を使用します; そうでない場合は、初期集合までシーケンスを展開する実装を使用します

## ノート

型フィールドは次のとおりです：

  * `N`  – ステップサイズの数値型
  * `AM` – 近似モデルの型
  * `RM` – 削減方法に関連する型
  * `S`  – `static`オプションに関連する値型
  * `R`  – `recursive`オプションに関連する値型

デフォルト値を持たない唯一のパラメータは、型パラメータ`N`に関連するステップサイズです。

デフォルトの近似モデルは

```julia
approx_model=CorrectionHull(order=10, exp=:base)
```

ここで、`CorrectionHull`は[AlthoffSB07](@citet)で説明されている区間行列近似法の実装を指します。区間行列演算に関する技術的な詳細については、パッケージ`IntervalMatrices.jl`を参照してください。

## 参考文献

このアルゴリズムの背後にある主なアイデアは[AlthoffSB07](@citet)にあります。これらの方法については、論文[Althoff10](@cite)で詳しく議論されています。

ゾノトープ次数削減方法に関しては、[Combastel03, Girard05](@citet)およびレビュー記事[YangS18](@cite)を参照してください。
