```
Amplitude(c::Circuit, states) -> Circuit
```

`states`の`Amplitude`測定を構築し、それを[`Circuit`](@ref) `c`の結果として追加します。

`states`は次の型である可能性があります：

  * `Vector{String}`
  * `String`

`states`のすべての要素は`'0'`または`'1'`でなければなりません。

# 例

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:3));

julia> c = Amplitude(c, "0000");
```
