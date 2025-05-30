```
LKJCholesky(d::Int, η::Real, uplo='L')
```

サイズ $d$ の `LKJCholesky` 分布は、形状パラメータ $\eta$ を持つ分布であり、$d\times d$ の実相関行列（対角に1がある正定値行列）の `LinearAlgebra.Cholesky` 因子分解に対する分布です。

この分布の変数またはサンプルは `LinearAlgebra.Cholesky` オブジェクトであり、`F = LinearAlgebra.cholesky(R)` によって返される可能性があります。したがって、`Matrix(F) ≈ R` は [`LKJ`](@ref) の変数またはサンプルです。

`LKJCholesky` のサンプリングは `LKJ` のサンプリングよりも速く、因子化された形で相関行列を持つことは、その後の計算を安価にすることがよくあります。

!!! note
    `LinearAlgebra.Cholesky` は、`F.U == F.L'` に関連する上部または下部の Cholesky 因子のいずれかを格納します。両方は `F.U` と `F.L` でアクセスできますが、格納されていない因子が要求されると、コピーが作成されます。`uplo` パラメータは、ランダムにサンプルを生成する際に上部（`'U'`）または下部（`'L'`）の Cholesky 因子が格納されるかを指定します。上部因子が必要な場合は、`uplo` を `'U'` に設定して、`F.U` を呼び出す際にコピーを割り当てないようにします。


詳細については [`LKJ`](@ref) を参照してください。

外部リンク

  * Lewandowski D, Kurowicka D, Joe H. Generating random correlation matrices based on vines and extended onion method, Journal of Multivariate Analysis (2009), 100(9): 1989-2001 doi: [10.1016/j.jmva.2009.04.008](https://doi.org/10.1016/j.jmva.2009.04.008)
