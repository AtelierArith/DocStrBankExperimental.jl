```
serialize(filename::AbstractString, object)
serialize(io::IO, object)
```

与えられた `object` を、Juliaのシリアル化を使用して `filename` または `io` に保存しますが、追加でPlutoのワークスペースモジュールを処理し、新しいセッションでデシリアライズできるようにします。
