matern(x, y, params)

σ² * \mathcal{M}_{ν}(||x-y||/ρ) を計算します。ここで、params = (σ, ρ, ν) であり、\mathcal{M} は Matern 共分散関数で、次のようにパラメータ化されています。

\mathcal{M}*{ν}(t) = σ^2 2^{1 - ν} Γ(ν)^{-1} (\sqrt{2 ν} t / ρ)^{ν} \mathcal{K}*{ν}(\sqrt{2 ν} t / ρ)。

詳細については、Stein (1999) の「Interpolation of Spatial Data: Some Theory for Kriging」を参照してください。
