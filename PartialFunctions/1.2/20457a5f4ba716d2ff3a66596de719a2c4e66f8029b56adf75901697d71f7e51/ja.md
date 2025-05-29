```
flip(f::Function)
```

引数を f から逆順で受け取る関数を作成します。つまり、最後の引数が最初に来て、その後に続きます。[`PartialFunctions.ReversedFunction{typeof(f)}`](@ref) を返します。ReversedFunction を反転させると、元の関数が返されます。

## 例

```jldoctest
julia> firstsecond(first, second) = (first = first, second = second)
firstsecond (generic function with 1 method)

julia> firstsecond("First thing", "Second thing")
(first = "First thing", second = "Second thing")

julia> using PartialFunctions

julia> secondfirst = flip(firstsecond);

julia> secondfirst("First thing", "Second thing")
(first = "Second thing", second = "First thing")
```
