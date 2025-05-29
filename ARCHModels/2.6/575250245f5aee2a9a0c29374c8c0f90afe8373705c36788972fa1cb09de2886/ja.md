```
predict(am::MultivariateARCHModel, what=:covariance)
```

`am`から1ステップ先の予測を形成します。`what`は予測されるオブジェクトを制御します。選択肢は`:covariance`（デフォルト）または`:correlation`です。
