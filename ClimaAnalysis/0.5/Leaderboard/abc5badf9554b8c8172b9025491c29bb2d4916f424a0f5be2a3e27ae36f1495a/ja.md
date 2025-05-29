```
Base.getindex(rmse_var::RMSEVariable, model_name, category)
```

指定された `model_name` と `category` によるルート平均二乗誤差を保持する配列のサブセットを返します。`String` と `Int` によるインデックス指定をサポートします。
