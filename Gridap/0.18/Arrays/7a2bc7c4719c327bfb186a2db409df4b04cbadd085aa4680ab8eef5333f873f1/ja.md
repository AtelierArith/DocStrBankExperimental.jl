```
Operation(op)
```

操作 `f` を一連のマップ `args` に適用した後の結果となるマップを返します。すなわち、`Operation(f)(args)(x...)` は形式的に `f(map(a->a(x...),args)...)` と定義されます。

# 例

```jldoctest
using Gridap.Arrays

fa(x) = x.*x
fb(x) = sqrt.(x)

x = collect(0:5)

fab = Operation(fa)(fb)
c = evaluate(fab,x)

println(c)

# 出力
[0.0, 1.0, 2.0, 3.0, 4.0, 5.0]
```
