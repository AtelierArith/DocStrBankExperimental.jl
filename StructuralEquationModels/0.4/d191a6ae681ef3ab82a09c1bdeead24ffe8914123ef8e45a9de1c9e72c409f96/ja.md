```
se_hessian(fit::SemFit; method = :finitediff)
```

ヘッセ行列に基づく標準誤差を返します。

# 引数

  * `method`: ヘッセ行列を計算する方法。オプションは次のとおりです。

      * `:analytic`: （モデルの解析的ヘッセ行列が計算できる場合のみ）
      * `:finitediff`: 有限差分近似用
