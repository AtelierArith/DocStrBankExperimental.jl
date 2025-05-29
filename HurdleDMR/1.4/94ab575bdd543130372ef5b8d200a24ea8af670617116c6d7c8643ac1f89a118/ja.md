```
fit(DMR,@model(c ~ x1*x2),df,counts; <keyword arguments>)
```

DMRを適合させますが、共変量行列の代わりにモデル式とデータフレームを取ります。 [`fit(::DMR)`](@ref)も参照してください。

`c`はカウントのモデルを示すために左辺に指定する必要があります。
