```
function set_limit!(CH::AbstractChart, limit::AbstractLimit)
function set_limit!(CH::AbstractChart, h::Float64)
function set_limit!(CH::MultipleControlChart, h::Vector{Float64})
function set_limit!(CH::MultipleControlChart, h::Float64)
function set_limit!(CH::MultipleControlChart, h::Float64, j::Int)
```

制御チャートの制御限界を設定します。

### 戻り値

新しい制御限界。
