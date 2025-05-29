レンズ評価

```julia
struct L end
function g(x, y)
  lens(L, (x = x, y = y))
  2x + y
end

  @leval L => println ∘ sum ∘ values g(1, 2)
```
