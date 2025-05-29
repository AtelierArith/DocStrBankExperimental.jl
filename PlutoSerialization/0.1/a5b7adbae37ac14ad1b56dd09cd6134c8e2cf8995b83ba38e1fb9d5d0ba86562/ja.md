```
deserialize(filename::AbstractString)
deserialize(io::IO)
```

`filename` または `io` を使用して、Juliaのシリアル化を用いてJuliaオブジェクトにデシリアライズしますが、Plutoのワークスペースモジュールを正しく処理します。
