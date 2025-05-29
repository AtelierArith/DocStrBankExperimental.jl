```
SignalNames(; x, u, y, name)
```

システム内の信号の名前を表す構造体。

  * `x::Vector{String}`: 状態変数の名前
  * `u::Vector{String}`: 入力変数の名前
  * `y::Vector{String}`: 出力変数の名前
  * `name::String`: システムの名前
