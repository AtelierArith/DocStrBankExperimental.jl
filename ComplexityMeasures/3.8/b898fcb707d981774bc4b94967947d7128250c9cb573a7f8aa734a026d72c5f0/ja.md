```
InformationMeasure
```

`InformationMeasure` はすべての情報測定 *定義* のスーパタイプです。

このパッケージでは、「情報測定」を確率質量関数（「離散」測定）または確率密度関数（「微分」測定）の関数として定義します。例としては、[`Shannon`](@ref) や [`Renyi`](@ref) のような（一般化された）エントロピー、または [`ShannonExtropy`](@ref) のようなエクストロピーがあります。[Amigó2018](@citet) は一般化されたエントロピーの有用なレビューを提供しています。

## 使用方法

以下にリストされている任意の情報測定は、次のように使用できます。

  * [`information`](@ref) を使用して、入力データに基づいて測定の数値を計算します。
  * [`information_maximum`](@ref) を使用して、測定の最大可能値を計算します。
  * [`information_normalized`](@ref) を使用して、測定の正規化された形式（最大可能値で割ったもの）を計算します。

[`information_maximum`](@ref)/[`information_normalized`](@ref) 関数は、測定の離散バージョンでのみ機能します。使用例については、上記の関数のドキュメント文字列を参照してください。

## 実装

  * [`Renyi`](@ref)。
  * [`Tsallis`](@ref)。
  * [`Shannon`](@ref)、これは上記の2つの特例で、限界 `q → 1` の場合です。
  * [`Kaniadakis`](@ref)。
  * [`Curado`](@ref)。
  * [`StretchedExponential`](@ref)。
  * [`RenyiExtropy`](@ref)。
  * [`TsallisExtropy`](@ref)。
  * [`ShannonExtropy`](@ref)、これは上記の2つの特例で、限界 `q → 1` の場合です。
  * [`FluctuationComplexity`](@ref)。

## 推定器

特定の情報測定は、離散定義と連続/微分定義の両方を持つ場合があり、それぞれ [`DifferentialInfoEstimator`](@ref) または [`DifferentialInfoEstimator`](@ref) を使用して推定されます。
