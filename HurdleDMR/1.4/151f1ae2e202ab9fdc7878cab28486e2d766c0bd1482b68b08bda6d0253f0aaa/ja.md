```
fit(CIR{DMR,FM},m,df,counts,projdir[,fmargs...]; <keyword arguments>)
```

@model() とデータフレームを使用し、共変量行列の代わりに依存変数を指定する projdir::Symbol を指定する fit(CIR{DMR,FM}...) のバージョンです。fit(CIR...) も参照してください。

# 例:

```julia
  m = fit(CIR{DMR,LinearModel}, @model(c~x1+x2), df, counts, :x1; nocounts=true)
```

ここで `c~` はカウントのモデルです。`x1`（`projdir`）は予測する変数です。データフレームを使用して予測することもできます。

```julia
  yhat = predict(m, df, counts)
  yhatnc = predict(m, df, counts; nocounts=true)
```
