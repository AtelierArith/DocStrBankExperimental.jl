```
Sequence(Ts|elements...) -> Construct{Tuple{Ts...}}
```

`elements`に基づいて構造データのシーケンスを定義します。

これは`Tuple{Ts...}`のデフォルトコンストラクタです。

# 例

```jldoctest
julia> serialize((true, 0x23))
2-element Vector{UInt8}:
 0x01
 0x23

julia> deserialize(Sequence(Bool, UInt8), b"\xab\xcd")
(true, 0xcd)
```

# 既知の問題

Julia 1.6では、`Sequence`要素の数が9を超えると、[`@construct`](@ref)がフィールドタイプを正しく推測できません。
