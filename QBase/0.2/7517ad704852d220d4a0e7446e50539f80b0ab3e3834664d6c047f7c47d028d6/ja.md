```
is_mixed(ρ :: State) :: Bool
```

`ρ`が混合状態である場合、すなわち`rank(ρ) > 1`である場合に`true`を返します。これは絶対許容誤差`ρ.atol`内での評価です。このメソッドは`Matrix`型にも使用できます。

```julia
is_mixed(ρ :: Matrix; atol=ATOL :: Float64) :: Bool
```
