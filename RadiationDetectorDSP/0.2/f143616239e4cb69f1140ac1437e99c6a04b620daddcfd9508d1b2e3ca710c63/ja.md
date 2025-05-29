```
abstract type AbstractRadSigFilter{FT<:FilteringType} <: Function
```

信号フィルタのための抽象型。

フィルタは `(flt::AbstractRadSigFilter)(input)` のように呼び出すことができ、特化したブロードキャスティングが付属しています。

`AbstractRadSigFilter` のサブタイプは次を実装しなければなりません。

```
fltinstance(flt::AbstractRadSigFilter, si::SamplingInfo)::[`AbstractRadSigFilterInstance`](@ref)
```

可逆フィルタは次も実装する必要があります。

  * `InverseFunctions.inverse(flt::SomeFilter)`

フィルタには逆が存在する場合がありますが、フィルタのパラメータによっては、追加のノイズがある場合に非常に不安定になる可能性があります。 ハイパス特性を持つフィルタは高周波ノイズを通過させるため、その逆もそのようなノイズを増幅せずに通過させます（実質的には）。 一方、ローパス特性を持つフィルタは高周波ノイズを減衰させるため、その逆はそのようなノイズを増幅し、実際のアプリケーションで信号をデコンボルブするのには通常役に立ちません。
