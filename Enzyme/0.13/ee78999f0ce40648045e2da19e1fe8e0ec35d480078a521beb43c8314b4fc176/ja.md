```
gradient!(::ReverseMode, dx, f, x)
```

配列入力関数 `f` の勾配を逆モードを使用して計算し、導関数の結果を既存の配列 `dx` に格納します。`x` と `dx` は同じ型の `Array` でなければなりません。

例:

```jldoctest gradip
f(x) = x[1]*x[2]

dx = [0.0, 0.0]
gradient!(Reverse, dx, f, [2.0, 3.0])

# 出力
([3.0, 2.0],)
```

```jldoctest gradip
dx = [0.0, 0.0]
gradient!(ReverseWithPrimal, dx, f, [2.0, 3.0])

# 出力
(derivs = ([3.0, 2.0],), val = 6.0)
```
