```
get_display_symbols(gate::AbstractGateSymbol; precision::Integer = 4,)::Vector{String}
```

`gate`を説明する`Vector{String}`のシンボルを返します。

`Vector`の各要素は、`gate`が作用するキュービットに関連付けられています。これは、回路図における`gate`の配置に役立ちます。オプションのパラメータ`precision`は、`gate`パラメータの小数点以下の桁数を設定することを可能にします。

# 例

```jldoctest
julia> get_display_symbols(get_gate_symbol(control_z(1, 2)))
2-element Vector{String}:
 "*"
 "Z"

julia> get_display_symbols(get_gate_symbol(phase_shift(1, π/2)), precision = 3)
1-element Vector{String}:
 "P(1.571)"

```
