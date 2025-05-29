```julia
coefnames(term)

```

TimeExpandedTermのcoefnamesは、基底関数の名前と項の名前および基底関数の列名のクロネッカー積を連結します。区切り文字は ' : ' です。firbasisのいくつかの例:         basis*313 : (Intercept) : 0.1         basis*313 : (Intercept) : 0.2         basis_313 : (Intercept) : 0.3         ...
