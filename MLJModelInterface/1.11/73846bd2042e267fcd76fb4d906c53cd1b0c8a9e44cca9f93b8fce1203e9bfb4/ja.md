```
decoder(x)
```

`CategoricalValue`の整数表現をデコードするための呼び出し可能なオブジェクトを返します。このオブジェクトは、`CategoricalValue` `x`と同じプールを共有します。具体的には、`decoder(x)(int(y)) == y`が成り立つすべての`CategoricalValue` `y`に対して成り立ちます。整数配列に対しても`decoder(x)`を呼び出すことができ、その場合`decoder(x)`はすべての要素に対してブロードキャストされます。

### 例

```julia-repl
julia> v = categorical(["c", "b", "c", "a"])
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "c"
 "b"
 "c"
 "a"

julia> int(v)
4-element Vector{UInt32}:
 0x00000003
 0x00000002
 0x00000003
 0x00000001

julia> d = decoder(v[3]);

julia> d(int(v)) == v
true
```

### 警告:

`int(d(u)) == u`が常に成り立つわけではありません。

参照: [`int`](@ref).
