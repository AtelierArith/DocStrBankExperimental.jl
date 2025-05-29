```
mvnormlogpdf(μ::A, LorU::A, x::A; ϵ = 1f-8) where A <: AbstractArray
```

バッチバージョンで、3Dテンソルを入力として受け取り、3次元の各スライスがバッチサンプルになります。 `μ` は (action*size x 1 x batchsize) 行列、`L` は (action*size x action*size x batchsize)、`x` は (action*size x action*samples x batchsize) です。 サイズ (1 x action*samples x batchsize) の3D行列を返します。
