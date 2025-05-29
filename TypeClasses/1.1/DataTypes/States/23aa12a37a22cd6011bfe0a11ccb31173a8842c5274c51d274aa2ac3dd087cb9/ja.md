```
getstate
```

`State` モナドの隠れた状態を返すための標準値。

## 例

```jldoctest
julia> using TypeClasses

julia> mystate = @syntax_flatmap begin
         state = getstate
         @pure println("state = $state")
       end;

julia> mystate(42)
state = 42
(nothing, 42)
```
