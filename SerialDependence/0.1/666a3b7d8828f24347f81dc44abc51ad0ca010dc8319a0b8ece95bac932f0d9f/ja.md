```
bootstrap_CI(Series, lags, coefficient, n_iter = 1000)
```

95%の信頼区間を提供します。'Series'を'n_iter'回シャッフルし、'coefficient'の値を計算し、上位および下位の2.5%の値を見つけて区間を取得します。これは'lags'の各ポイントについて行われます（'Series'が長い場合はコストがかかる可能性があります）。

入力 :     - Series : カテゴリデータの入力配列     - coef*func (**function**) : CIを計算する必要がある関数。             'coefficient'は次の**関数**のいずれかである必要があります : 'cramer*coefficient, cohen*coefficient, theils*U'。     - lags (Array{Int64,1}) : 分析が行われるラグ値     - n_iter (Int64) : ブートストラップ手順のために実行される反復回数。 戻り値 :     - top (Array{Float64,1}) : CIの上限の値の配列。     - bottom (Array{Float64,1}) : CIの下限の値の配列。
