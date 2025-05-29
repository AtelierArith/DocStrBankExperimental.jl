```
time_rate(tree::T, f::Function, δt::Float64) where {T <: iT}
```

木全体で `δt` ごとにサンプリングされた時刻で `f` 関数から値を抽出します。
