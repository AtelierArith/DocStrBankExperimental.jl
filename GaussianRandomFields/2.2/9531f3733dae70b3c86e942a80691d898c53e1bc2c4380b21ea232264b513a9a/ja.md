```
GaussianRandomField([mean,] cov, generator, pts...)
GaussianRandomField([mean,] cov, generator, nodes, elements)
```

平均 `mean` と共分散構造 `cov` が定義された点 `pts` でガウス乱数場を計算し、ガウス乱数場生成器 `generator` を使用して計算します。

# 例

```jldoctest label2
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn 共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> mean = fill(π, (51, 51));

julia> grf = GaussianRandomField(mean, cov, Cholesky(), pts, pts)
ガウス乱数場は、Cholesky分解を使用して、51×51の構造化グリッド上の2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0) です。

```

`mean` が指定されていない場合、ゼロ平均のガウス乱数場が仮定されます。

```jldoctest label2
julia> grf = GaussianRandomField(cov, Cholesky(), pts, pts)
ガウス乱数場は、Cholesky分解を使用して、51×51の構造化グリッド上の2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0) です。

```

ガウス乱数場生成器 `generator` は `Cholesky()`, `Spectral()`, `KarhunenLoeve(n)`（ここで `n` は展開の項数）、または `CirculantEmbedding()` であることができます。点 `pts` は `AbstractVector` 型の引数として指定でき、その場合はテンソル（クロネッカー）積が仮定されるか、ノードテーブル `nodes` と要素テーブル `elements` を持つ有限要素メッシュとして指定できます。

```jldoctest label2
julia> grf = GaussianRandomField(cov, KarhunenLoeve(500), pts, pts)
ガウス乱数場は、500項のKL展開を使用して、51×51の構造化グリッド上の2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0) です。

julia> exponential_cov = CovarianceFunction(2, Exponential(.1))
2d 指数共分散関数 (λ=0.1, σ=1.0, p=2.0)

julia> grf = GaussianRandomField(exponential_cov, CirculantEmbedding(), pts, pts)
ガウス乱数場は、循環埋め込みを使用して、51×51の構造化グリッド上の2d 指数共分散関数 (λ=0.1, σ=1.0, p=2.0) です。

```

分離可能なガウス乱数場は `SeparableCovarianceFunction` を使用して定義できます。

```jldoctest label2
julia> separable_cov = SeparableCovarianceFunction(Exponential(.1), Exponential(.1))
2d 分離可能共分散関数 [ 指数 (λ=0.1, σ=1.0, p=2.0), 指数 (λ=0.1, σ=1.0, p=2.0) ]

julia> grf = GaussianRandomField(separable_cov, KarhunenLoeve(500), pts, pts)
ガウス乱数場は、500項のKL展開を使用して、51×51の構造化グリッド上の2d 分離可能共分散関数 [ 指数 (λ=0.1, σ=1.0, p=2.0), 指数 (λ=0.1, σ=1.0, p=2.0) ] です。

julia> plot_eigenfunction(grf, 3);

```

異方性乱数場のサポートも提供しています。

```jldoctest label2
julia> anisotropic_cov = CovarianceFunction(2, AnisotropicExponential([500 400; 400 500]))
2d 異方性指数共分散関数 (A=[500 400; 400 500], σ=1.0)

julia> grf = GaussianRandomField(anisotropic_cov, CirculantEmbedding() , pts, pts)
ガウス乱数場は、循環埋め込みを使用して、51×51の構造化グリッド上の2d 異方性指数共分散関数 (A=[500 400; 400 500], σ=1.0) です。

julia> heatmap(grf);

```

不規則な領域の場合、有限要素メッシュの `nodes` と `elements` を含む行列として点を指定します。要素の中心で乱数場の値を計算するには、オプションのキーワード `mode="center"` を使用します。

```jldoctest label2
julia> nodes, elements = Lshape();

julia> grf = GaussianRandomField(cov, Spectral(), nodes, elements)
ガウス乱数場は、スペクトル分解を使用して、998点と1861要素を持つメッシュ上の2d Matérn共分散関数 (λ=0.3, ν=1.0, σ=1.0, p=2.0) です。

```

代わりに、サイズ `N` x `d` の `Matrix{T}` を渡して、与えられた点の集合によって定義された非構造化グリッドで乱数場を計算します。

乱数場からのサンプルは `sample` 関数を使用して計算できます。

```jldoctest label2
julia> sample(grf);

```

参照: [`Cholesky`](@ref), [`Spectral`](@ref), [`KarhunenLoeve`](@ref), [`CirculantEmbedding`](@ref), [`sample`](@ref)
