```
submit!(job::Job)
submit!(args_of_Job...; kwargs_of_Job...)
```

ジョブをキューに送信します。

> `submit!(Job(...))` は `submit!(...)` に簡略化できます。両者は同等です。


関連情報は [`Job`](@ref), [`@submit`](@ref) を参照してください。
