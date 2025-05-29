---

```
Notifier.notify(message; title="Julia", sound=false, time=4, logo)
```

デスクトップ通知で通知します。

# 引数

  * `sound::Union{Bool, AbstractString}`: デフォルトの音を再生するか、特定の音を再生します。
  * `time::Real`: 表示時間。
  * `logo`: デフォルトはJuliaのロゴです。
