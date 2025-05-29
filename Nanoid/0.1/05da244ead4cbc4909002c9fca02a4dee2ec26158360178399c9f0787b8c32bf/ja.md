```
nanoid(size::Integer = 21; alphabet::String = "") -> String
```

指定されたサイズとアルファベットでランダムなNanoidを生成します。サイズはデフォルトで21、アルファベットはURLセーフのアルファベットがデフォルトです。

## 例

```jldoctest
julia> nanoid()
"tcDIFxMJHw6UgUnbI_6za"

julia> nanoid(10)
"OutzQWa1SB"

julia> nanoid(; alphabet = "ABCDEFGHIJ")
"GEHCAGFJIAHCJGIHHIHFF"

julia> nanoid(10; alphabet = "abcdef")
"abeafebaab"
```
