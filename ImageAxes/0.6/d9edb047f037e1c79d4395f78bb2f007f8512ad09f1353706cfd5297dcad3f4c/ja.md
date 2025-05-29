```
HasTimeAxis{AA}
```

型 `AA` が時間軸を持っているかどうかをテストするためのトレイトです。時間軸は使用する前に宣言する必要があります。

# 例

```julia
using ImageAxes, SimpleTraits

# `:time` という名前のすべての軸が時間軸であることを宣言します
@traitimpl TimeAxis{Axis{:time}}

# 時間軸を持つか持たないかに基づいてディスパッチする関数を定義します
@traitfn got_time{AA<:AxisArray;  HasTimeAxis{AA}}(img::AA) = "はい、時間があります"
@traitfn got_time{AA<:AxisArray; !HasTimeAxis{AA}}(img::AA) = "いいえ、忙しすぎます"

julia> A = AxisArray(1:5, Axis{:time}(1:5));

julia> got_time(A)
"はい、時間があります"

julia> A = AxisArray(1:5, Axis{:x}(1:5));

julia> got_time(A)
"いいえ、忙しすぎます"
```
