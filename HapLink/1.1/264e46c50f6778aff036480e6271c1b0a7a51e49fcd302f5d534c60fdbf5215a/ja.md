```
quality(vc::VariationCall) -> Union{Nothing,Float64}
```

`vc`の平均phred品質スコアを取得します。未知の場合は`nothing`を返します。

関連情報としては、[`quality(::VariationInfo)`](@ref)、[`quality(::VariationPileup)`](@ref)があります。
