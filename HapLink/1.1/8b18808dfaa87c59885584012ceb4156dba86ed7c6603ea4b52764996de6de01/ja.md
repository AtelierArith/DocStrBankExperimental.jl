```
strand_bias(vc::VariationCall) -> Union{Nothing,Float64}
```

`vc`が正のストランドに出現する割合を取得します。未知の場合は`nothing`を返します。

関連情報としては、[`strand(::VariationInfo)`](@ref)、[`strand(::VariationPileup)`](@ref)があります。
