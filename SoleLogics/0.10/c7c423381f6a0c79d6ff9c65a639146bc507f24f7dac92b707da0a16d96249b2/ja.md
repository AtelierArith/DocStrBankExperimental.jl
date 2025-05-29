```
check(a::Atom, i::AbstractVector)
```

渡されたベクターにその [`Atom`](@ref) が含まれているかどうかを示す真偽値を返します。

# 例

```julia-repl
julia> check(Atom(1), [1,2,4])
true

julia> check(Atom(5), [2,3,4])
false
```

他に [`Atom`](@ref) も参照してください。
