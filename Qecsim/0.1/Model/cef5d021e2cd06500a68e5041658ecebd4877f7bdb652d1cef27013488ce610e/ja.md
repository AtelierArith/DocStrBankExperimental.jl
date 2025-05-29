```
DecodeResult(
    success::Union{Nothing,Bool},
    recovery::Union{Nothing,AbstractVector{Bool}},
    logical_commutations::Union{Nothing,AbstractVector{Bool}}
    custom_values::Union{Nothing,AbstractVector}
)
DecodeResult(;
    success::Union{Nothing,Bool}=nothing,
    recovery::Union{Nothing,AbstractVector{Bool}}=nothing,
    logical_commutations::Union{Nothing,AbstractVector{Bool}}=nothing
    custom_values::Union{Nothing,AbstractVector}=nothing
)
```

[`decode`](@ref) によって返されるデコード結果を構築します。

通常、デコーダは `recovery` 操作を提供し、`success` と `logical_commutations` の評価をクライアントに委任します。例えば、[`App`](@ref App) のように。オプションとして、`success` および/または `logical_commutations` をオーバーライドとして提供することができます。成功値を解決するためには、`recovery` または `success` のいずれかを指定する必要があります。さらに、`custom_values` を指定することもできます。`logical_commutations` および/または `custom_values` が提供される場合、それらは同一のパラメータ化されたシミュレーション実行において一貫した型とサイズである必要があります。例えば、[`App`](@ref App) は実行を通じて `logical_commutations` を合計し、同様に、`custom_values` が数値であればそれらは実行を通じて合計され、配列であれば `vcat` を使用して連結されます。

[`decode`](@ref) も参照してください。

# 例

```jldoctest
julia> DecodeResult(; recovery=BitVector([1, 0, 1, 0, 1, 1]))  # 一般的な使用例
DecodeResult{Nothing}(nothing, Bool[1, 0, 1, 0, 1, 1], nothing, nothing)

julia> DecodeResult(; success=true)  # 成功をオーバーライド
DecodeResult{Nothing}(true, nothing, nothing, nothing)

julia> DecodeResult(; success=false, logical_commutations=BitVector([1, 0]))  # すべてをオーバーライド
DecodeResult{Nothing}(false, nothing, Bool[1, 0], nothing)

julia> DecodeResult(; success=true, custom_values=[2.3, 4.1])  # カスタム値（数値）
DecodeResult{Vector{Float64}}(true, nothing, nothing, [2.3, 4.1])

julia> DecodeResult(; success=true, custom_values=[[2.3], [4.1]])  # カスタム値（配列）
DecodeResult{Vector{Vector{Float64}}}(true, nothing, nothing, [[2.3], [4.1]])

julia> DecodeResult(true, nothing, nothing, [2.3, 4.1])  # 位置パラメータ
DecodeResult{Vector{Float64}}(true, nothing, nothing, [2.3, 4.1])

julia> DecodeResult(; success=nothing, recovery=nothing)  # 指定されたパラメータが少なすぎる
ERROR: QecsimError: 'success' または 'recovery' のいずれかを指定する必要があります
Stacktrace:
[...]
```
