```
colorize(krs::AbstractVector{<:KRatios}, red::Element, green::Element, blue::Element, normalize=:All[|:Each])
colorize(krs::AbstractVector{<:KRatios}, elms::AbstractVector{Element}, normalize=:All)
```

最大3つの`Element`からRGBカラー化された画像を作成します。要素は、`krs`内のすべての`KRatios`に対して正規化されます。結果の画像は、微量元素の視覚化を可能にするために、係数`scale`でスケーリングされます。
