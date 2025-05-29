```
Base.setindex!(rmse_var::RMSEVariable, rmse, model_name::String)
```

`rmse_var`のルート平均二乗誤差の配列に、配列から値を格納します。`String`によるインデックス指定をサポートします。線形インデックス指定はサポートしません。
