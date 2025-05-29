```
SlabBuffer(;finalize::Bool = true)
```

サイズが1048576のスラブを持つスラブアロケータを作成します。`finalize`キーワード引数を`false`に設定すると、`SlabBuffer`の使用が終わったときに明示的に`Bumper.free()`を呼び出す必要があります。これは推奨されません。
