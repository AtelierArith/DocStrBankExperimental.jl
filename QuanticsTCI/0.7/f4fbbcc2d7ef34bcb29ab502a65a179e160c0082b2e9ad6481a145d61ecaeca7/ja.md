```
function quanticsfouriermpo(
    R::Int;
    sign::Float64=-1.0,
    maxbonddim::Int=12,
    tolerance::Float64=1e-14,
    K::Int=25,
    method::Symbol=:SVD,
    normalize::Bool=true
)::TCI.TensorTrain{ComplexF64}
```

量子フーリエ変換演算子をテンソル列形式で生成します。量子テンソル列 $F_{\boldsymbol{\sigma}}$ と収束させると、結果は関数のフーリエ変換であり、量子テンソル列形式で表されます。$\tilde{F}_{\boldsymbol{\sigma}'} = \sum_{\boldsymbol{\sigma}} F_{\boldsymbol{\sigma}} \exp(-2\pi i (k_{\boldsymbol{\sigma'}}-1) (m_{\boldsymbol{\sigma}} - 1)/M)$、ここで $k_{\boldsymbol{\sigma}} = \sum_{\ell=1}^R 2^{R-\ell} \sigma_\ell$、$m_{\boldsymbol{\sigma}'} = \sum_{\ell=1}^R 2^{R-\ell} \sigma'_\ell$、および $M=2^R$ です。

!!! note "インデックスの順序"
    フーリエ変換の前に、最も左のインデックスは $\sigma_1$ に対応し、これは最も大きな長さスケールを表し、最も右のインデックスは $\sigma_R$ に対応し、これは最も小さな長さスケールを表します。フーリエ変換された QTT のインデックス $\sigma_1' \ldots \sigma_{R}'$ は *逆* の順序で整列されています。つまり、最も左のインデックスは $\sigma'_R$ に対応し、これは最も小さな長さスケールを表します。これにより、小さなボンド次元の演算子を構築することができます（参照1を参照）。必要に応じて、`TCI.reverse(tt)` を呼び出すことで、大から小へのインデックスの順序を復元できます。


フーリエ変換演算子は、Chen と Lindsey によるテンソル列の直接的な解析的構築を使用して実装されています（参照2を参照）。このようにして得られたテンソル列は、ユーザーが指定したボンド次元と許容誤差に再圧縮されます。

引数:

  * `R`: フーリエ変換のビット数。
  * `sign`: 指数 $\exp(2i\pi \times \mathrm{sign} \times (k_{\boldsymbol{\sigma'}}-1) (x_{\boldsymbol{\sigma}}-1)/M)$ の符号、通常は $\pm 1$。
  * `maxbonddim`: 演算子を圧縮するためのボンド次元。観察によれば、`maxbonddim = 12` は一般的に `1e-12` の精度に達するのに十分です。
  * `tolerance`: TT 圧縮の許容誤差。フーリエ変換の誤差は一般的にこの誤差許容範囲よりも少し大きいことに注意してください。
  * `K`: 圧縮前の TT のボンド次元、すなわちフーリエ変換を近似するための基底関数の数（参照2を参照）。`K < 22` の場合、TT は不正確になります。非常に高い精度が必要な場合は、より高い値が必要になることがあります。
  * `method`: TT を圧縮するための方法。`:SVD` と `:CI` の間で選択します。
  * `normalize`: 演算子を等長写像として正規化するかどうか。

!!! details "参考文献"
    1. [J. Chen, E. M. Stoudenmire, and S. R. White, Quantum Fourier Transform Has Small Entanglement, PRX Quantum 4, 040318 (2023).](https://link.aps.org/doi/10.1103/PRXQuantum.4.040318)
    2. [J. Chen and M. Lindsey, Direct Interpolative Construction of the Discrete Fourier Transform as a Matrix Product Operator, arXiv:2404.03182.](http://arxiv.org/abs/2404.03182)

