```
struct RCFilter <: AbstractRadII>RFilter
```

一次のRCローパスフィルターです。

逆フィルターは[`InvCRFilter`](@ref)ですが、追加のノイズがある場合には不安定であることに注意してください。RCフィルターは高周波ノイズを減衰させるため、その逆はそのようなノイズを増幅し、実際のアプリケーションで信号をデコンボルブするのには通常役に立ちません。

コンストラクタ:

  * `RCFilter(fields...)`

フィールド:

  * `rc::Union{Real, Unitful.AbstractQuantity{<:Real}}`: RC時定数
