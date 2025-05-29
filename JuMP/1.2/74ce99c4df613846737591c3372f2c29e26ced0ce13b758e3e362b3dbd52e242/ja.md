```
@NLobjective(model, sense, expression)
```

`model`に非線形目的関数を追加します。最適化の感覚`sense`は`Max`または`Min`でなければなりません。

# 例

```
@NLobjective(model, Max, 2x + 1 + sin(x))
```
