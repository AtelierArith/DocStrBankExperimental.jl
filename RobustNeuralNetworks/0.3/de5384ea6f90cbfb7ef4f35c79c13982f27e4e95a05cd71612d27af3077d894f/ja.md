```
set_output_zero!(m::AbstractLBDNParams)
```

LBDNの出力マップをゼロに設定します。

結果として得られたモデルが次のように呼び出されると 

```julia
lbdn = LBDN(m)
y = lbdn(u)
```

任意の`u`に対して`y = 0`となります。
