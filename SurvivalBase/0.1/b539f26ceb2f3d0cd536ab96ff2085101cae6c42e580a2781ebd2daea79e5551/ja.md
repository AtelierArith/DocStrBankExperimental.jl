```
Surv(T::Symbol, Δ::Symbol)
```

`SurvTerm`オブジェクトを作成し、通常は左辺にある式の構築において変数のタプル`(T,Δ)`を保持します。これは、右検閲された出力時間`T`とそのステータス指示子`Δ`を表します：Δが真であることは、時間が実際に観測されたことを意味し、偽であることは検閲を意味します。

この情報は、通常、式の左側にあり、推定器に依存する動作を持ちます。これにより、次のように[`StatsModels.jl`](https://github.com/JuliaStats/StatsModels.jl)からの式を使用することができます：

```
@formula(Surv(time,status) ~ covariate1 + covariate 2)
```

この使用法は、例えばコックスモデルで一般的です。ただし、式の*意味*はモデルに大きく依存することに注意してください：ハザード回帰と最大尤度推定では、同じことを意味しません。
