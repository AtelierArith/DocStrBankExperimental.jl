```
amplitude_matrix(𝐓::AbstractTransitionMatrix{CT, N}, ϑᵢ, φᵢ, ϑₛ, φₛ; λ=2π)
```

与えられたT行列`𝐓`の振幅行列を、与えられた入射角と散乱角で計算します。

パラメータ：

  * `𝐓`: 散乱体のT行列。
  * `ϑᵢ`: ラジアンでの入射天頂角。
  * `φᵢ`: ラジアンでの入射方位角。
  * `ϑₛ`: ラジアンでの散乱天頂角。
  * `φₛ`: ラジアンでの散乱方位角。
  * `λ`: ホスト媒質における入射波の波長。デフォルトは2πです。

一般的なT行列の場合、Mishchenko et al. (2002)の式(5.11) – 式(5.17)がフォールバックとして使用されます。

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
+T_{m n m^{\prime} n^{\prime}}^{21} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \tau_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc}}\right)+T_{m n m^{\prime} n^{12}}^{12} \tau_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right) \\
\left.+T_{m n m^{\prime} n^{\prime}}^{22} \pi_{m n}\left(\vartheta^{\text {sca }}\right) \pi_{m^{\prime} n^{\prime}}\left(\vartheta^{\text {inc }}\right)\right] \exp \left[\mathrm{i}\left(m \varphi^{\text {sca }}-m^{\prime} \varphi^{\text {inc }}\right)\right], \\
\end{array}
$$

ここで

$$
\begin{array}{l}
\alpha_{m n m^{\prime} n^{\prime}}=\mathrm{i}^{n^{\prime}-n-1}(-1)^{m+m^{\prime}}\left[\frac{(2 n+1)\left(2 n^{\prime}+1\right)}{n(n+1) n^{\prime}\left(n^{\prime}+1\right)}\right]^{1 / 2}, \\
\pi_{m n}(\vartheta)=\frac{m d_{0 m}^n(\vartheta)}{\sin \vartheta}, \quad \pi_{-m n}(\vartheta)=(-1)^{m+1} \pi_{m n}(\vartheta), \\
\tau_{m n}(\vartheta)=\frac{\mathrm{d} d_{0 m}^n(\vartheta)}{\mathrm{d} \vartheta}, \quad \tau_{-m n}(\vartheta)=(-1)^m \tau_{m n}(\vartheta)
\end{array}
$$

```
