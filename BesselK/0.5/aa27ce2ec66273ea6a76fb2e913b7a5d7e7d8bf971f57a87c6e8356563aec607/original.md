matern(x, y, params)

computes σ² * \mathcal{M}_{ν}(||x-y||/ρ), where params = (σ, ρ, ν) and \mathcal{M} is the Matern covariance function, parameterized as

\mathcal{M}*{ν}(t) = σ^2 2^{1 - ν} Γ(ν)^{-1} (\sqrt{2 ν} t / ρ)^{ν} \mathcal{K}*{ν}(\sqrt{2 ν} t / ρ).

For more information, see Stein (1999), Interpolation of Spatial Data: Some Theory for Kriging.
