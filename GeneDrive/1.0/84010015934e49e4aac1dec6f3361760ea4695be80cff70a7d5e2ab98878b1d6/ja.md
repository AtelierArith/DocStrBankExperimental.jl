```
get_temperature_response(::Float64, response::NoResponse, ::Float64) = response.baseline_value
```

温度応答のない `NoResponse` データを返します。
