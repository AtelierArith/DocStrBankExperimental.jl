```
uconvertp(u::Units, x)
uconvertp(u::MixedUnits, x)
```

一般的に、これは [`Unitful.uconvert`](@ref) と同じです。単位変換がさらなる情報なしでは曖昧になる場合（例：`uconvert(dB, 10)`）、`uconvertp` は比率が電力量であると仮定します。

この関数を不注意に使用すると、誤った計算につながる可能性があることに注意することが重要です。`Quantity{<:Gain}` 型を考慮してください：`-20dB/m` を `0.1/m` に変換するのは魅力的ですが、これは `-20dB/m` とは根本的に異なる意味を持ちます。長さに `0.1/m` を掛けて指数減衰を計算しようとするとどうなるかを考えてみてください。

例：

```jldoctest
julia> using Unitful

julia> uconvertp(u"dB", 10)
10.0 dB

julia> uconvertp(NoUnits, 20u"dB")
100.0
```
