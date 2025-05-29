```
fit(CIR{HDMR,FM},m,df,counts,projdir[,fmargs...]; <keyword arguments>)
```

@model() とデータフレームを受け取り、covars 行列の代わりに使用する fit(CIR{HDMR,FM}...) のバージョンであり、projdir::Symbol は従属変数を指定します。fit(CIR...) も参照してください。

# 例:

```julia
  m = fit(CIR{HDMR,LinearModel}, @model(h~x1+x2, c~x1), df, counts, :x1; nocounts=true)
```

ここで `h~` はゼロのモデル、`c~` は正のモデルです。`x1` (`projdir`) は予測する変数です。データフレームを使って予測することもできます。

```julia
  yhat = predict(m, df, counts)
  yhatnc = predict(m, df, counts; nocounts=true)
```
