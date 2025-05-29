```
DataLoader(ensemble_solution)
```

`EnsembleSolution`のための`DataLoader`のインスタンスを作成します。

`EnsembleSolution`は、パッケージ[`GeometricSolutions.jl`](https://github.com/JuliaGNI/GeometricSolutions.jl)からインポートされます。

# 引数

この`DataLoader`のファンクタには、キーワード引数として

  * `autoencoder = false` と
  * `suppress_info = false` があります。

[`DataLoader(::AbstractArray{<:Number, 3})`](@ref)のドキュメントを参照してください。

# 実装

内部的には、データはテンソルとして保存され、第三軸の長さはアンサンブル内の解の数に等しくなります。
