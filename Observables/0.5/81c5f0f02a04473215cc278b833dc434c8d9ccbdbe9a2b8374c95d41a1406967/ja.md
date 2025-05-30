```
obs = Observable(val; ignore_equal_values=false)
obs = Observable{T}(val; ignore_equal_values=false)
```

`Ref`のようですが、ハンドラを追加することで更新を監視できます [`on`](@ref) または [`map`](@ref) を使用して。`ignore_equal_values=true`を設定すると、`isequal(observable[], new_value)`が真である場合に`observable[] = new_value`のイベントがトリガーされません。
