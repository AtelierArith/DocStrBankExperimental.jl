```julia
calcProductGaussians(
    M,
    μ_,
    Σ_;
    μ0,
    Λ_,
    weight,
    do_transport_correction
)

```

入ってくるガウス点の共分散加重平均を $μ_$ と座標共分散 $Σ_$ の積として計算します。

ノート

  * 加重平均と新しい共分散（同型積）を両方返します。
  * より効率的なヘルパー関数は、代わりにキーワード逆共分散 `Λ_` を渡すことを許可します。
  * `size(Σ_[1],1) == manifold_dimension(M)` を仮定します。
  * まずラムダを計算し、次に平均の積を計算します。
  * https://ccrma.stanford.edu/~jos/sasp/Product*Two*Gaussian_PDFs.html
  * Pennec, X. Intrinsic Statistics on Riemannian Manifolds: Basic Tools for Geometric Measurements, HAL Archive, 2011, Inria, France.

開発ノート:

  * FIXME 製品が異なる接空間からの共分散を含むため、平行輸送は必要ですか？
  * TODO 常に共分散行列の逆を再計算するのを避ける
