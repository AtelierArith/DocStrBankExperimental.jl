```
start_reading(d::AbstractDiskDataProvider)
```

バッファへの読み込みを初期化します。この関数はデータセットが使用される前に呼び出す必要があります。データセットに対して `stop!` を呼び出すまで、読み込みは続きます。データセットが [`ChannelDiskDataProvider`](@ref) の場合、これは問題ありません。
