```
generate_binomials(F::System)
```

入力多項式系から Binomial*system*data ラッパーオブジェクトを返します。$Log|C|$-リフティングによって誘導された混合セルから得られた二項系です。オブジェクト Binomial*system*data には、二項系、法線ベクトル、リフティングベクトル、および計算された混合細分からのセルが含まれています。オブジェクト Binomial*system*data は、rph_track 関数の入力として使用されます。

# 引数

  * `F` : 実多面体ホモトピーの対象系。

```julia
B = generate_binomials(F)
```

```
Binomial_system_data
```

```julia
B.binomial_system
```

```
2-element Vector{Any}:
 Expression[-24000*y + x^3, 50*x*y - y^2]
 Expression[-24000*y + x^3, -9 + 50*x*y]
```
