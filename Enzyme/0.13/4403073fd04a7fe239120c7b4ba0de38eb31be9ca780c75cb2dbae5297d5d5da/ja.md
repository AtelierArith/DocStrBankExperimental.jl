```
gradient(::ForwardMode, f, x; shadows=onehot(x), chunk=nothing)
```

配列入力関数 `f` の勾配を前方モードを使用して計算します。オプションのキーワード引数 `shadow` は、戻り値にフォワード伝播するために使用される型 `x` のワンホットベクトルのベクトルです。パフォーマンスの理由から、これは `gradient` への呼び出しの外で一度計算されるべきです。

例:

```jldoctest gradfwd
f(x) = x[1]*x[2]

gradient(Forward, f, [2.0, 3.0])

# output

([3.0, 2.0],)
```

```jldoctest gradfwd
gradient(ForwardWithPrimal, f, [2.0, 3.0])

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```

```jldoctest gradfwd
gradient(Forward, f, [2.0, 3.0]; chunk=Val(1))

# output

([3.0, 2.0],)
```

```jldoctest gradfwd
gradient(ForwardWithPrimal, f, [2.0, 3.0]; chunk=Val(1))

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```

AbstractArray またはスカラーを返す関数に対して、この関数は形状が `(size(output)..., size(input)...)` の AbstractArray を返します。この関数によって返される AbstractArray の型については、現在のところ保証はありません（提供された場合、入力 AbstractArray と同じであるかどうかは不明です）。

他の型を返す関数に対して、この関数は出力型の値の形状 `size(input)` の AbstractArray を返します。

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = gradient(Forward, f, [2.0, 3.0, 4.0])

# output
([3.0 2.0 0.0; 0.0 1.0 1.0],)
```

この関数は複数の引数をサポートし、それぞれに対して勾配を計算します。

```jldoctest gradfwd2
mul(x, y) = x[1]*y[2] + x[2]*y[1]

gradient(Forward, mul, [2.0, 3.0], [2.7, 3.1])

# output

([3.1, 2.7], [3.0, 2.0])
```

これは、導関数が必要ない場合にいくつかの引数を `Const` としてマークする機能を含み、対応する導関数マップでは何も返しません。

```jldoctest gradfwd2
gradient(Forward, mul, [2.0, 3.0], Const([2.7, 3.1]))

# output

([3.1, 2.7], nothing)
```
