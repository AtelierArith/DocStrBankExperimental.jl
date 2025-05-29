```
mvnormlogpdf(μ::AbstractVecOrMat, L::AbstractMatrix, x::AbstractVecOrMat)
```

多変量正規分布のlogpdf関数のGPU互換で自動微分可能なバージョン。入力として、平均ベクトル`mu`、共分散行列のコレスキー分解の下三角行列`L`、および各列がサンプルであるサンプルの行列`x`を取ります。`μ`および`Σ = L*L'`でパラメータ化された`MvNormal`のために、`x`の各列のlogpdfを含むベクトルを返します。
