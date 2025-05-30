```
get_display_symbols(::Readout; precision::Integer = 4,)::Vector{String}
```

`Readout`を説明するシンボルの`Vector{String}`を返します。

`Vector`の各要素は、`Readout`が作用するキュービットに関連付けられています。これは、回路図における`Readout`の配置に役立ちます。オプションのパラメータ`precision`は、`Readout`には影響を与えません。

# 例

```jldoctest
julia> get_display_symbols(readout(2, 2))
1-element Vector{String}:
 "✲"

```
