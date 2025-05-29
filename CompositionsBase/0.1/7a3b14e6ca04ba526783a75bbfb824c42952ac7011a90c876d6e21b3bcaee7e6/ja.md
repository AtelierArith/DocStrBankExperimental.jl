```
g ⨟ f
opcompose(g, f)
```

逆合成演算子は次のように定義されます。

```
g ⨟ f = f ∘ g
⨟(f) = f
⨟(fs...) = ∘(reverse(fs)...)
```
