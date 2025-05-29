```
SpinWaveTheoryKPM(sys::System; measure, regularization=1e-8, tol=nothing,
                  niters=nothing, niters_bounds=10, method=:lanczos)
```

[`SpinWaveTheory`](@ref) の変種で、反復行列-ベクトル積を使用して [`intensities`](@ref) を推定します。直接的な行列対角化を避けることで、この方法は計算コストを立方体から線形スケーリングに削減します。大きなシステムサイズは、例えば、クエンチされた乱れのモデルや、ほぼ非整合な秩序波ベクトルを持つモデルで発生する可能性があります。

計算コストは $𝒪(N M + M^2)$ のようにスケールします。反復回数 $M$ は `niters` パラメータで直接指定できます。あるいは、無次元の誤差許容値 `tol` を指定することもでき、`M ≈ -2 \log_{10}(tol) Δϵ / fwhm` となります。ここで `Δϵ` は励起の推定スペクトル帯域幅で、`fwhm` はユーザーが提供する広がり `kernel` の半値全幅です。`tol` の一般的な選択肢は `0.05`（より速い）または `0.01`（より正確）です。`tol` または `niters` のいずれかが必要です。パラメータ `niters_bounds` は、スペクトル境界を推定するために使用されるクリロフ部分空間の次元を選択します。

!!! warning "精度に関する考慮事項"
    エネルギー空間の解像度は、反復回数 $M$ に反比例してスケールします。このような広がりの誤差は、通常、許容値パラメータ `tol` を介してうまく制御できます。より深刻な問題は、小さな励起エネルギーを持つバンドでの強度損失です。例えば、ゴールドストーンモードの近くで発生します。特定のケースでは、この欠落した強度は、反復回数 $M$ を増やすことで修正できない数値的な丸め誤差によるものです。


2つの `method` オプションが利用可能で、`:lanczos` と `:kpm` です。一般的にランチョスが好まれます。なぜなら、与えられた反復回数に対してほぼ最適な精度を達成するからです [1, 2]。ランチョスの実装は、歴史的に興味深いかもしれないカーネル多項式法 [3] を使用した以前の研究に基づいています。

## 参考文献

1. [T. Chen, *The Lanczos algorithm for matrix functions: a handbook for scientists* (2024) [arXiv:2410.11090]](https://arxiv.org/abs/2410.11090).
2. [N. Amsel, T. Chen, A. Greenbaum, C. Musco, C. Musco, *Near-Optimal Approximation of Matrix Functions by the Lanczos Method* (2023) [arXiv:2303.03358]](https://arxiv.org/abs/2303.03358).
3. [H. Lane et al., *Kernel Polynomial Method for Linear Spin Wave Theory* (2023) [arXiv:2312.08349]](https://arxiv.org/abs/2312.08349).
