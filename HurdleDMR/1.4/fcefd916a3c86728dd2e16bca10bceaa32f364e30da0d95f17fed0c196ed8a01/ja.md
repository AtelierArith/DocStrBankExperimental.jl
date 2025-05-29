```
fit(::CIR{BM,FM},covars,counts,projdir[,fmargs...]; <keyword arguments>)
```

`covars[:,projdir] ~ counts + covars[:,~projdir]` の逆回帰モデル (CIR) をフィットします。

CIR は三つのステップから成ります：

1. 後方回帰モデル BM<:DCR をフィットします: counts ~ covars
2. projdir の方向における十分な削減射影を計算します
3. 前方回帰モデル FM<:RegressionModel をフィットします:

```
covars[:,projdir] ~ srproj(counts) + covars[:,~projdir]
```

# 例:

```julia
  m = fit(CIR{DMR,LinearModel}, covars, counts, 1; nocounts=true)
  yhat = predict(m, covars, counts)
  yhatnc = predict(m, covars, counts; nocounts=true)
```

# 引数

  * `covars` n-by-p の共変量行列
  * `counts` n-by-d のカウント行列 (通常はスパース)
  * `projdir` 前方モデルで従属変数として使用される共変量列のインデックス
  * `fmargs...` 前方回帰モデルに渡されるオプション引数

# キーワード

  * `nocounts::Bool=false` カウントなしのベンチマークモデルもフィットするかどうか
  * `bmkwargs...` 後方回帰モデルに渡されるキーワード引数
