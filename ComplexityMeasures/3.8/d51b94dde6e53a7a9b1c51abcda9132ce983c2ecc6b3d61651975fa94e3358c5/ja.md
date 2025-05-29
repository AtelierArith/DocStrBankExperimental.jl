```
エンコーディング
```

すべてのエンコーディングスキームのスーパークラス。エンコーディングは常に入力データの要素を正の整数にエンコードします。エンコーディングAPIは、関数[`encode`](@ref)と[`decode`](@ref)によって定義されています。一部の確率推定器は、内部でエンコーディングを利用します。

現在利用可能なエンコーディングは次のとおりです：

  * [`OrdinalPatternEncoding`](@ref)。
  * [`GaussianCDFEncoding`](@ref)。
  * [`RectangularBinEncoding`](@ref)。
  * [`RelativeMeanEncoding`](@ref)。
  * [`RelativeFirstDifferenceEncoding`](@ref)。
  * [`UniqueElementsEncoding`](@ref)。
  * [`BubbleSortSwapsEncoding`](@ref)。
  * [`PairDistanceEncoding`](@ref)。
  * [`CombinationEncoding`](@ref)、これは上記のいずれかのエンコーディングを組み合わせることができます。
