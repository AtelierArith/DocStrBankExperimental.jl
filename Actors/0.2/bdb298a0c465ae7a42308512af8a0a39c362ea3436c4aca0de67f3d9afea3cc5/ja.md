```
exec(lk::Link, from::Link, f, args...; kwargs...)
exec(lk::Link, f, args...; timeout::Real=5.0, kwargs...)
exec(name::Symbol, ....)
```

アクター `lk`（または登録されている場合は `name`）に任意の関数を実行させ、その返された値を [`Response`](@ref) として送信します。

# 引数

  * アクター `lk::Link` または登録されている場合は `name::Symbol`、
  * `from::Link`: `Response` を送信するリンク。
  * `f`: 呼び出し可能なオブジェクト、
  * `args...; kwargs...`: それに対する引数とキーワード引数、
  * `timeout::Real=5.0`: 秒単位のタイムアウト。タイムアウトを望まない場合は `timeout=Inf` に設定します。

**注意:** `from` が省略された場合、`exec` はブロックし、待機して結果を返します（`timeout` 付き）。
