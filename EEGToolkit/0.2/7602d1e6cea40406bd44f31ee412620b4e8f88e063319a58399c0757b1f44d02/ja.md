`sigma_index(x::Vector{<:AbstractFloat}, fs::Integer)`

$$
\sigma
$$

-インデックスアルゴリズム [(Huupponen et al., 2007)](https://pubmed.ncbi.nlm.nih.gov/17555950/) は、スピンドル周波数帯域における異常に高い振幅値を見つけます。EEGの1秒間のウィンドウごとに、次のことを計算します。

  * スピンドル周波数帯域における最大振幅、これを $S_{max}$ と呼びます
  * 低アルファおよびシータ周波数における平均振幅、これを

$$
\alpha_{mean}, \theta_{mean}
$$

  * 最大アルファ振幅 $\alpha_{max}$

各ウィンドウの$\sigma$-インデックスは、$\alpha_{max} > S_{max}$ の場合はゼロと定義され、それ以外の場合は

$$
f(S_{max}, \alpha_{mean}, \phi_{mean}) = \frac{2S_{max}}{ \alpha_{mean} + \theta_{mean} } 
$$

高い値は、より高いスピンドル確率を示します。元の論文で推奨されている拒否閾値は $\lambda = 4.5$ です。
