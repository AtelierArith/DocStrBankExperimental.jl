```
colreduce(f::Function, data::DataSet{<:ConTab}; coln = nothing)
```

各テーブルの行を合計し、各列に合計が配置された新しいテーブルを作成します。
