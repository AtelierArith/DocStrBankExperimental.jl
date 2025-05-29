```
evaluate(m, x)
```

`TPS` 関数 `m` を結果 `x` で評価します。

# 引数

  * `m::Union{TPS,AbstractArray{TPS{T,D}}}`    – 評価する `TPS` または `TPS` マップ
  * `x::Union{Number,AbstractArray{<:Number}}` – `m` を評価する変数の値

`Evaluate` は `m` を「呼び出す」ことによっても呼び出すことができます。例えば、`m(x)`、`m([x[1], x[2], ...])`、または `m(x[1], x[2], ...)` も許可されています。
