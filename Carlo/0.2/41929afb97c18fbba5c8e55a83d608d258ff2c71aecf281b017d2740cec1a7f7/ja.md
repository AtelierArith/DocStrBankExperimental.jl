```
evaluate!(func::Function, eval::AbstractEvaluator, name::Symbol, (ingredients::Symbol...))
```

`name`という評価可能な量を定義します。これは、観測可能な平均値`ingredients...`に依存します。関数`func`は、材料をパラメータとして受け取り、評価可能な値を返す必要があります。カルロは、結果ファイルに観測可能な値と共に表示される正しい誤差バーを持つバイアス補正された結果を計算するためにジャックナイフ法を実行します。
