```
gradient(::ReverseMode, f, args...)
```

実数値関数 `f` の勾配を逆モードを使用して計算します。微分可能な各引数について、この関数は新しい導関数オブジェクトを割り当てて返し、各引数の導関数のタプルを返します。引数が微分不可能な場合、返されるタプルの要素は何もありません。

逆モードでは（ここでは）、導関数は元の引数と同じ型になります。

これは構造体の勾配です。構造体 `x` に対して、勾配の成分を含む同じ型の別のインスタンスを返します。結果において、`grad.a` は任意の微分可能な `x.a` に対して `∂f/∂x.a` を含み、他の型に対しては `grad.c == x.c` になります。

例:

```jldoctest gradient
f(x) = x[1]*x[2]

grad = gradient(Reverse, f, [2.0, 3.0])

# output
([3.0, 2.0],)
```

```jldoctest gradient
grad = gradient(Reverse, only ∘ f, (a = 2.0, b = [3.0], c = "str"))

# output

((a = 3.0, b = [2.0], c = "str"),)
```

```jldoctest gradient
mul(x, y) = x[1]*y[1]

grad = gradient(Reverse, mul, [2.0], [3.0])

# output
([3.0], [2.0])
```

```jldoctest gradient

grad = gradient(Reverse, mul, [2.0], Const([3.0]))

# output
([3.0], nothing)
```

原始値を返すモード（例: ReverseWithPrimal）を渡す場合、返される型はタプルになり、最初の要素には導関数が含まれ、2番目の要素には元の計算の結果が含まれます。

```jldoctest gradient

grad = gradient(ReverseWithPrimal, f, [2.0, 3.0])

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```

```jldoctest gradient

grad = gradient(ReverseWithPrimal, mul, [2.0], [3.0])

# output
(derivs = ([3.0], [2.0]), val = 6.0)
```

```jldoctest gradient
grad = gradient(ReverseWithPrimal, mul, [2.0], Const([3.0]))

# output
(derivs = ([3.0], nothing), val = 6.0)
```
