```
amplitude_matrix(𝐓::AbstractTransitionMatrix{CT, N}, ϑᵢ, φᵢ, ϑₛ, φₛ; λ=2π)
```

Calculate the amplitude matrix of the given T-Matrix `𝐓` at the given incidence and scattering angles. 

Parameters:

  * `𝐓`: the T-Matrix of the scatterer.
  * `ϑᵢ`: the incidence zenith angle in radians.
  * `φᵢ`: the incidence azimuthal angle in radians.
  * `ϑₛ`: the scattering zenith angle in radians.
  * `φₛ`: the scattering azimuthal angle in radians.
  * `λ`: the wavelength of the incident wave in the host medium. Default to 2π.

For a general T-Matrix, Eq. (5.11) – Eq. (5.17) in Mishchenko et al. (2002) is used as a fallback.

$$
\begin{array}{l}
S_{11}\left(\hat{\mathbf{n}}^{\text {sca }}, \hat{\mathbf{n}}^{\text {inc }}\right)=\frac{1}{k_1} \sum_{n=1}^{\infty} \sum_{n^{\prime}=1}^{\infty} \sum_{m=-n}^n \sum_{m^{\prime}=-n^{\prime}}^{n^{\prime}} \alpha_{m n m^{\prime} n^{\prime}}\left[T_{m n m^{\prime} n^{\prime}}^{11} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right. \\
+T_{m n m^{\prime} n^{\prime}}^{21} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\mathrm{inc}}\right)+T_{m n m^{\prime} n^{\prime}}^{12} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\mathrm{inc}}\right) \\
\left.+T_{m n m^{\prime} n^2}^{22} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right] \exp \left[\mathrm{i}\left(m \varphi^{\text {sca }}-m^{\prime} \varphi^{\text {inc }}\right)\right] \text {, } \\
S_{12}\left(\hat{\mathbf{n}}^{\mathrm{sca}}, \hat{\mathbf{n}}^{\mathrm{inc}}\right)=\frac{1}{\mathrm{i} k_1} \sum_{n=1}^{\infty} \sum_{n^{\prime}=1}^{\infty} \sum_{m=-n}^n \sum_{m^{\prime}=-n^{\prime}}^{n^{\prime}} \alpha_{m n m^{\prime} n^{\prime}}\left[T_{m n m^{\prime} n^{\prime}}^{11} \pi_{m n}\left(\vartheta^{\mathrm{sca}}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\mathrm{inc}}\right)\right. \\
+T_{m n m^{\prime} n^{\prime}}^{21} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\mathrm{inc}}\right)+T_{m n m^{\prime} n^{\prime}}^{12} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right) \\
\left.+T_{m n m^{\prime} n^{\prime}}^{22} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right] \exp \left[\mathrm{i}\left(m \varphi^{\text {sca }}-m^{\prime} \varphi^{\text {inc }}\right)\right] \text {, } \\
S_{21}\left(\hat{\mathbf{n}}^{\mathrm{sca}}, \hat{\mathbf{n}}^{\mathrm{inc}}\right)=\frac{\mathrm{i}}{k_1} \sum_{n=1}^{\infty} \sum_{n^{\prime}=1}^{\infty} \sum_{m=-n}^n \sum_{m^{\prime}=-n^{\prime}}^{n^{\prime}} \alpha_{m n m^{\prime} n^{\prime}}\left[T_{m n m^{\prime} n^{\prime}}^{11} \tau_{m n}\left(\vartheta^{\mathrm{sca}}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\mathrm{inc}}\right)\right. \\
+T_{m n m^{\prime} n^{\prime}}^{21} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\mathrm{inc}}\right)+T_{m n m^{\prime} n^{\prime}}^{12} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right) \\
\left.+T_{m n m^{\prime} n^{\prime}}^{22} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right] \exp \left[\mathrm{i}\left(m \varphi^{\text {sca }}-m^{\prime} \varphi^{\text {inc }}\right)\right] \text {, } \\
S_{22}\left(\hat{\mathbf{n}}^{\text {sca }}, \hat{\mathbf{n}}^{\mathrm{inc}}\right)=\frac{1}{k_1} \sum_{n=1}^{\infty} \sum_{n^{\prime}=1}^{\infty} \sum_{m=-n}^n \sum_{m^{\prime}=-n^{\prime}}^{n^{\prime}} \alpha_{m n m^{\prime} n^{\prime}}\left[T_{m n n^{\prime} n^{\prime}}^{11} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right. \\
+T_{m n m^{\prime} n^{\prime}}^{21} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)+T_{m n m^{\prime} n^{12}}^{12} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right) \\
\left.+T_{m n m^{\prime} n^{\prime}}^{22} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right] \exp \left[\mathrm{i}\left(m \varphi^{\text {sca }}-m^{\prime} \varphi^{\text {inc }}\right)\right], \\
\end{array}
$$

Where

$$
\begin{array}{l}
\alpha_{m n m^{\prime} n^{\prime}}=\mathrm{i}^{n^{\prime}-n-1}(-1)^{m+m^{\prime}}\left[\frac{(2 n+1)\left(2 n^{\prime}+1\right)}{n(n+1) n^{\prime}\left(n^{\prime}+1\right)}\right]^{1 / 2}, \\
\pi_{m n}(\vartheta)=\frac{m d_{0 m}^n(\vartheta)}{\sin \vartheta}, \quad \pi_{-m n}(\vartheta)=(-1)^{m+1} \pi_{m n}(\vartheta), \\
\tau_{m n}(\vartheta)=\frac{\mathrm{d} d_{0 m}^n(\vartheta)}{\mathrm{d} \vartheta}, \quad \tau_{-m n}(\vartheta)=(-1)^m \tau_{m n}(\vartheta)
\end{array}
$$
