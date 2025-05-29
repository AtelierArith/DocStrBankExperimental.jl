```
RectangularBinEncoding <: Encoding
RectangularBinEncoding(binning::RectangularBinning, x)
RectangularBinEncoding(binning::FixedRectangularBinning)
```

点 `χ ∈ x` をヒストグラムビンに [`encode`](@ref) するエンコーディングスキームです。

最初の呼び出しシグネチャは単に [`FixedRectangularBinning`](@ref) を初期化し、次に2番目の呼び出しシグネチャを呼び出します。

点をビンにマッピングする情報については、[`FixedRectangularBinning`](@ref) を参照してください。
