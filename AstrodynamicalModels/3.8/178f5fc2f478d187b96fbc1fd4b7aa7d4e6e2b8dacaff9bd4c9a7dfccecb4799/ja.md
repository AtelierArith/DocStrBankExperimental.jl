```julia
AttitudeFunction(; stm, name, kwargs...)

```

宇宙船の姿勢ダイナミクスのための `ODEFunction` を返します。

# 拡張ヘルプ

### 使用法

`stm` と `name` のキーワード引数は `Attitude` に渡されます。他のすべてのキーワード引数は直接 `SciMLBase.ODEFunction` に渡されます。

```julia
f = AttitudeFunction()
let u = randn(7), p = randn(15), t = NaN # 時間不変
    f(u, p, t)
end
```
