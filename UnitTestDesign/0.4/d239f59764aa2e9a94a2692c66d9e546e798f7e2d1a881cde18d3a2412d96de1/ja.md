```
full_factorial(parameters...)
full_factorial(parameters...; disallow = filter_function)
```

パラメータのすべての組み合わせに対してテストケースを生成します。

# 例

```julia
full_factorial([0.1, 0.2, 0.3], ["low", "high"], [false, true])
```

フィルタ関数を指定すると、許可されていない組み合わせが削除されます。
