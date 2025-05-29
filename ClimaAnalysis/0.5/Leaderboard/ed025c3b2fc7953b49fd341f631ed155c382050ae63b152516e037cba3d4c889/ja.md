```
Base.getindex(rmse_var::RMSEVariable, model_name::String)
```

`model_name`で指定されたルート平均二乗誤差を保持する配列のサブセットを返します。`String`によるインデックス指定をサポートします。線形インデックス指定はサポートしません。
