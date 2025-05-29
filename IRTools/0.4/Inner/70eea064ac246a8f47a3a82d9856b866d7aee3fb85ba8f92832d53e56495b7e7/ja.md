```
insert!(ir, v, x)
```

与えられたIRに式または文`x`を変数`v`が定義される直前に挿入し、`x`の新しい変数を返します。詳細は[`insertafter!`](@ref)を参照してください。

```
julia> f(x) = 3x + 2
f (generic function with 1 method)

julia> ir = @code_ir f(1)
1: (%1, %2)
  %3 = 3 * %2
  %4 = %3 + 2
  return %4

julia> insert!(ir, IRTools.var(4), :(println("hello, world")))
%5

julia> ir
1: (%1, %2)
  %3 = 3 * %2
  %5 = println("hello, world")
  %4 = %3 + 2
  return %4
```
