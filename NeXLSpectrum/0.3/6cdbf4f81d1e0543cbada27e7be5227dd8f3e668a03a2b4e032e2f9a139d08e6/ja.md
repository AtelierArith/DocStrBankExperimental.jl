```
estimatebackground(data::AbstractArray{Float64}, channel::Int, width::Int=5, order::Int=2)
```

チャネルを中心としたカウントデータに対する二次フィットの接線を返します。幅は指定された値です。
