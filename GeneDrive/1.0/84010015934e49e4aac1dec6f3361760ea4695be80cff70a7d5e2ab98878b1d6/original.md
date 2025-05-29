```
get_temperature_response(::Float64, response::NoResponse, ::Float64) = response.baseline_value
```

Return `NoResponse` data (model without temperature response).
