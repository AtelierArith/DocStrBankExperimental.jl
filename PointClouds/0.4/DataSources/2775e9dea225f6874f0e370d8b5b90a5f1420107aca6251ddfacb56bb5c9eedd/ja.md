```
LAS(t::PointCloudTile; kws...)
```

`PointCloudTile`の点群データをロードし、必要に応じてファイルをダウンロードします。ダウンロードされたファイルは、[BaseDirs.jl](https://github.com/tecosaur/BaseDirs.jl)によって提供されるユーザーのキャッシュディレクトリに保存され、今後はそこからロードされます。キーワード引数については、[`Base.read(url, LAS)`](@ref Base.read(::IO, ::Type{PointClouds.LAS}))を参照してください。
