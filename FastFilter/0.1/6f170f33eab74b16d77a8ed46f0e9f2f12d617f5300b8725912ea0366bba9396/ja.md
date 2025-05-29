`BinaryFuseFilter{T}( 	keys::Vector{UInt64};  	seed = UInt64(0x726b2b9d438b9d4d),  	max_iterations = 10) where T <: Union{UInt8, UInt16, UInt32}`

`keys` から T 型のフィンガープリントを持つバイナリフィルターを構築します。

## 引数

`seed` は初期シード値として使用され、構造の構築ステップ中に反復的に変更されます。

`max_iterations` は、終了する前に試みる構築ステップのラウンド数を制限します。

# 例

```julia-repl
julia> filter = BinaryFuseFilter{UInt8}(UInt64.[1:10])
BinaryFuseFilter with 10 keys and seed 1198702242888554850.

julia> UInt64(1) in filter
true

julia> UInt64(11) in filter
false
```
