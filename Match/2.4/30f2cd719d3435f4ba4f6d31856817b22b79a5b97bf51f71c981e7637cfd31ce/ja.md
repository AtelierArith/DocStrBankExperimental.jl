```
@match_return value
```

@match ケースの結果部分内で、指定された値を早期に返すことができます。

# 例

```julia-repl
julia> struct Vect
           x
           y
       end

julia> function norm(v)
           @match v begin
               Vect(x, y) => begin
                   if x==0 && y==0
                       @match_return v
                   end
                   l = sqrt(x^2 + y^2)
                   Vect(x/l, y/l)
                   end
               _ => v
           end
       end
norm (generic function with 1 method)

julia> norm(Vect(2, 3))
Vect(0.5547001962252291, 0.8320502943378437)

julia> norm(Vect(0, 0))
Vect(0, 0)
```
