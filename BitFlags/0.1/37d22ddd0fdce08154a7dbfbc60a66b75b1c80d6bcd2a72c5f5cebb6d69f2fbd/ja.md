```
@bitflag BitFlagName[::BaseType] value1[=x] value2[=y]
```

`BitFlagName`という名前の`BitFlag{BaseType}`サブタイプを作成し、オプションで割り当てられた値`x`と`y`を持つフラグメンバー値`value1`と`value2`を持ちます。`BitFlagName`は他の型と同様に使用でき、フラグメンバー値は通常の値として使用できます。例えば、

# 例

```jldoctest itemflags
julia> @bitflag Items apple=1 fork=2 napkin=4

julia> f(x::Items) = "I'm a flag with value: $x"
f (generic function with 1 method)

julia> f(apple)
"I'm a flag with value: apple"

julia> f(apple | fork)
"I'm a flag with value: (apple | fork)"
```

値は`begin`ブロック内でも指定できます。例えば、

```julia
@bitflag BitFlagName begin
    value1
    value2
end
```

`BaseType`はデフォルトで[`UInt32`](@ref)であり、`Unsigned`のプリミティブサブタイプでなければなりません。メンバー値はビットフラグ型と`BaseType`の間で変換できます。`read`と`write`はこれらの変換を自動的に行います。非デフォルトの`BaseType`でビットフラグが作成された場合、`Integer(value1)`は`BaseType`の型を持つ整数`value1`を返します。

ビットフラグのすべてのインスタンスをリストするには`instances`を使用します。例えば、

```jldoctest itemflags
julia> instances(Items)
(apple::Items = 0x00000001, fork::Items = 0x00000002, napkin::Items = 0x00000004)
```
