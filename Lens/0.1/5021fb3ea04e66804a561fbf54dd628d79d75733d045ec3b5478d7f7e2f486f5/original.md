Function call with lens (shorthand for)

```julia
f(x) = lens(:mylens, 2x + 1)
lmap = (mylens = println,)
@lenscall lmap f(31)
```
