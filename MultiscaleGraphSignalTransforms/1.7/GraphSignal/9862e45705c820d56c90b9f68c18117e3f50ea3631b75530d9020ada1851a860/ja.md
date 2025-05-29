```
replace_data!(G::GraphSig, newdata::Matrix{Float64})
```

GraphSigオブジェクトのデータを置き換えます

### 入力引数

  * `G::GraphSig`: データを置き換える入力GraphSigオブジェクト; この関数の実行後にさまざまなフィールドが更新されます
  * `newdata::Matrix{Float64}`: 新しいデータ（行列である必要があります）
