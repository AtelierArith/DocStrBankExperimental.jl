```
DataLoader(solution)
```

`GeometricSolution`のための`DataLoader`のインスタンスを作成します。

`GeometricSolution`は、パッケージ[`GeometricSolutions.jl`](https://github.com/JuliaGNI/GeometricSolutions.jl)からインポートされます。

# 引数

この[`DataLoader`](@ref)のファンクタは、キーワード引数として

  * `autoencoder = false` と
  * `suppress_info = false` を持っています。

[`DataLoader(::AbstractArray{<:Number, 3})`](@ref)のドキュメントを参照してください。

# 実装

内部的には、データはテンソルとして保存され、第三軸の長さは1です。
