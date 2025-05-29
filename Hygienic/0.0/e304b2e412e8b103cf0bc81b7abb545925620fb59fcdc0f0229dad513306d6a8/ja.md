```
@hygienize(ex::Expr)
```

変数定義をgensymされたシンボルに置き換えることで引用を変換するマクロです。

```julia
julia> using Hygienic

julia> @hygienize quote
           x = 1
           x + y
       end
quote
    #= REPL[2]:2 =#
    var"##x#274" = 1
    #= REPL[2]:3 =#
    var"##x#274" + y
end
```
