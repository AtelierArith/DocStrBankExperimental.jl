```
@trace f(args...)
@trace P f(args...)
```

`f`の型付きトレースを取得します。これは`@code_typed`に類似しています。`@code_typed`とは異なり、値ではなく型を渡すことをお勧めします。例えば：

```
julia> @trace ::Int + ::Int
1: (%1 :: const(+), %2 :: Int64, %3 :: Int64)
  %4 = (+)(%2, %3) :: Int64
  return %4
```

もし実際の整数を渡すと、Mjolnirはそれらを積極的に定数伝播させ、トリビアルなトレースになります。

```
julia> @trace 2+2
1: (%1 :: const(+), %2 :: const(2), %3 :: const(2))
  return 4
```

`P`は使用されるプリミティブセットで、デフォルトでは`Mjolnir.Defaults()`です。
