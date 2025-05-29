レンズを使った関数呼び出し（省略形）

```julia
f(x) = lens(:mylens, 2x + 1)
lmap = (mylens = println,)
@lenscall lmap f(31)
```
