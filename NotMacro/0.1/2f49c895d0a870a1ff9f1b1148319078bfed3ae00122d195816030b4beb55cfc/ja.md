@not someboolean

`!`の人間が読みやすい代替手段

## 例

```jldoctest
julia> using NotMacro

julia> if @not isodd(2) && @not iseven(3) && true
           println("works")
       end
works

julia> @macroexpand if @not isodd(2) & @not iseven(3) & true
           println("works")
       end
:(if !(isodd(2)) & (!(iseven(3)) & true)
      #= none:2 =#
      println("works")
  end)
```
