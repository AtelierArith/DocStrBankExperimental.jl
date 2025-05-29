```
radius(x)
```

`x`の半径であり、`issubset_interval(x, mid(x) ± radius(x))`が成り立ちます。`x`が複素数の場合、半径は実部と虚部の最大半径です。

IEEE Standard 1788-2015の`rad`関数を実装します（表9.2）。

参照: [`inf`](@ref), [`sup`](@ref), [`bounds`](@ref), [`mid`](@ref), [`diam`](@ref) および [`midradius`](@ref)。
