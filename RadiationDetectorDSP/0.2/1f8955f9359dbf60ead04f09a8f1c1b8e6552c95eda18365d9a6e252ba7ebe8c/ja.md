```
struct CRFilter <: AbstractRadIIRFilter
```

一次のCRハイパスフィルターです。

逆フィルターは[`InvCRFilter`](@ref)であり、これは通常、追加のノイズが存在しても安定しています。これは、CRフィルターが高周波ノイズを通過させるため、その逆もノイズを増幅することなく通過させるからです。

コンストラクタ:

  * `CRFilter(fields...)`

フィールド:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR時間定数
