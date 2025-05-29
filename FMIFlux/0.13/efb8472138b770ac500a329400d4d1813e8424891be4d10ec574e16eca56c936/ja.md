非推奨:

```
fmi2InputDoStepCSOutput(comp::FMU2Component, 
                        dt::Real, 
                        u::Array{<:Real})
```

すべてのFMU入力を`u`に設定し、´´´fmi2DoStep´´´を実行し、すべてのFMU出力を返します。
