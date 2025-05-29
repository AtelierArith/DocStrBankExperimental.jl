```
GroupViaHistogram(binning::FixedRectangularBinning)
```

[`AttractorsViaFeaturizing`](@ref)で特徴をグループ化する方法に関する指示を含む構造体を初期化します。`GroupViaHistogram`は特徴空間でヒストグラムを実行します。次に、同じヒストグラムビンにあるすべての特徴は同じラベルを取得します。`binning`はComplexityMeasures.jlの[`FixedRectangularBinning`](@ref)のインスタンスです。（`RectangularBinning`を許可しない理由は、継続中にビンが同一であることを保証する必要があるためです）。
