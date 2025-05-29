```
update_wtmat!(m::WSVarLmmModel)
```

パラメータ値 `m.τ` と `m.Lγ` に従って観測重み行列を更新します。WLS によって `m.β` を更新し、それに応じて残差を更新します。目的関数、勾配、およびヘッセ行列を評価するために必要なさまざまなオブジェクトを事前に計算して保存します。戻り値として、

  * `m.data[i].∇β  = Xi' inv(Vi) ri`
  * `m.data[i].Hββ = Xi' inv(Vi) Xi`
  * `m.∇β  = sum_i Xi' inv(Vi) ri`
  * `m.Hββ = sum_i Xi' inv(Vi) Xi`
