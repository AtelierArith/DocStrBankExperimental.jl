```
adapt_to_input(f::F, example_input::T) where {F,T}
```

`f`と同じ操作を行う関数を生成しますが、これは`example_input`の型とサイズ、そして`example_input`が存在する計算デバイスに最適化/特化されています。

最適化/特化された`f`のバージョンを返すか、これが不可能な場合は[`UnadaptedFunction{F,T}(f)`](@ref)を返します。
