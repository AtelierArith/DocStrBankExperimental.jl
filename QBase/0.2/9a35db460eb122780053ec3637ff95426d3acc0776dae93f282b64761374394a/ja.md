```
is_pure(ρ :: State) :: Bool
```

`ρ`が純粋である場合、すなわち`rank(ρ) == 1`である場合に`true`を返します。これは絶対許容誤差`ρ.atol`内でのことです。このメソッドは`Matrix`型にも使用できます。

```julia
is_pure(ρ :: Matrix; atol=ATOL :: Float64) :: Bool
```
