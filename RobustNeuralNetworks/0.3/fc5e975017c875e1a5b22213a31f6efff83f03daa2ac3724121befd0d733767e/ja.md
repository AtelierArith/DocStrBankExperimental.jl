```
set_output_zero!(m::AbstractRENParams)
```

RENの出力マップをゼロに設定します。

結果として得られるモデルが次のように呼び出されると

```julia
ren = REN(m)
x1, y = ren(x, u)
```

任意の`x`および`u`に対して`y = 0`となります。
