```
writesamples(data::Matrix{Int},
             [model::Union{MPS, MPO, LPDO, Nothing},]
             output_path::String)
```

データとモデルをファイルに保存します：

# 引数：

  * `data`: 測定データの配列
  * `model`: （オプション）MPS、MPO、またはChoi
  * `output_path`: ファイルへのパス
