```
NBP_pN_A_J23E_J23M_J2S_threads!(dq, q, params, t)
```

マルチスレッド太陽系（JPL DE430/431）動的モデル。モデルで考慮される天体は、太陽、8つの惑星、月、およびJPL DE430エフェメリスに含まれる343の主帯小惑星です。考慮される効果は次のとおりです：

  * すべての天体間のポストニュートン点質量加速度： https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract のページ7の式(35)を参照

$$
\begin{align*}
    \mathbf{a}_i & = \sum_{j\neq i}\frac{\mu_j(\mathbf{r}_j - \mathbf{r}_i)}{r_{ij}^3}
    \left\lbrace
    1 - \frac{4}{c^2}\sum_{l\neq i}\frac{\mu_l}{r_{il}} - \frac{1}{c^2}\sum_{k\neq j}\frac{\mu_k}{r_{jk}} + \left(\frac{\dot{s}_i}{c}\right)^2 + 2\left(\frac{\dot{s}_j}{c}\right)^2
    - \frac{4}{c^2}\mathbf{v}_i\cdot\mathbf{v}_j - \frac{3}{2c^2}\left[\frac{(\mathbf{r}_i - \mathbf{r}_j)\cdot\mathbf{v}_j}{r_{ij}}\right]^2 + \frac{1}{2c^2}(\mathbf{r}_j - \mathbf{r}_i)\cdot\mathbf{a}_j
    \right\rbrace \\
    & \hspace{0.5cm} + \frac{1}{c^2}\sum_{j\neq i} \frac{\mu_j}{r_{ij}^3}[(\mathbf{r}_i - \mathbf{r}_j)\cdot(4\mathbf{v}_i - 3\mathbf{v}_j)](\mathbf{v}_i - \mathbf{v}_j)
    + \frac{7}{2c^2}\sum_{j\neq i}\frac{\mu_j\mathbf{a}_j}{r_{ij}},
\end{align*}
$$

ここで、$\mathbf{v}_i = \dot{\mathbf{r}}_i$、$\dot{s}_i = ||\mathbf{v}_i||^2$、および$\mathbf{a}_i = \ddot{\mathbf{r}}_i$です。

  * 地球の形状効果（扁平率）($J_2$および$J_3$)、
  * 太陽の$J_2$効果、および
  * 月の$J_2$および$J_3$効果： https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract のページ13の式(28)および https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract のページ33の式(173)および(174)を参照

$$
\left[
\begin{array}{c}
    \ddot{\xi} \\
    \ddot{\eta} \\
    \ddot{\zeta} \\
\end{array}
\right]
=
-\frac{GM}{r^2}
\left\lbrace
\sum_{n=2}^{n_1} J_n\left(\frac{R}{r}\right)^n
\left[
\begin{array}{c}
    (n+1)P_n(\sin\phi) \\
    0 \\
    -\cos\phi P_n'(\sin\phi) \\
\end{array}
\right]
+\sum_{n=2}^{n_2} \left(\frac{R}{r}\right)^n\sum_{m=1}^n
\left[
\begin{array}{c}
    -(n+1)P_n^m(\sin\phi)[+C_{nm}\cos m\lambda + S_{nm}\sin m\lambda] \\
    m\sec\phi P_n^m(\sin\phi)[-C_{nm}\sin m\lambda + S_{nm}\cos m\lambda] \\
    \cos\phi P'\,_n^m(\sin\phi)[+C_{nm}\cos m\lambda + S_{nm}\sin m\lambda] \\
\end{array}
\right]
\right\rbrace,
$$

ここで、$r$は2つの天体間の重心の分離距離です；$n_1$および$n_2$はそれぞれのゾナルおよびテッセラル展開の最大次数です；$P_n(\sin\phi)$は次数$n$のレジェンドル多項式、$P_n^m(\sin\phi)$は次数$n$および順序$m$の関連レジェンドル関数、$J_n$は拡張体のゾナル調和係数です；$C_{nm}$、$S_{nm}$は拡張体のテッセラル調和係数、$R$は拡張体の赤道半径、$\phi$は調和が表現される体固定座標系に対する点質量の緯度です；$\lambda$は同じ体固定座標系における点質量の東経です。プライムは引数$\sin\phi$に関する微分を示します。加速度は適切な回転行列を適用することによって慣性系に変換されます。

  * 地球の姿勢の歳差と揺動のための運動モデル（IAU 1976/1980地球姿勢モデル）： [`c2t_jpl_de430`](@ref)を参照。
  * 月の姿勢のための運動モデル（Seidelmann et al., 2006）： https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract のページ9の式(14)-(15)およびページ16の式(34)-(35)を参照。

$$
\textbf{月のマントル}
$$

$$
\begin{align*}
    \dot{\phi}_m & = (\omega_{m,x}\sin\psi_m + \omega_{m,y}\cos\psi_m)/\sin\theta_m \\
    \dot{\theta}_m & = \omega_{m,x}\cos\psi_m - \omega_{m,y}\sin\psi_m \\
    \dot{\psi}_m & = \omega_{m,z} - \dot{\phi_m}\cos\theta_m
\end{align*}
$$

および

$$
    \dot{\mathbf{\omega}}_m = \mathbf{I}_m^{-1}\left\lbrace
        \sum_{A\neq M} \mathbf{N}_{M,fig M- pmA} + \mathbf{N}_{M,figM-figE} - \dot{\mathbf{I}}_m\mathbf{\omega}_m - \mathbf{\omega}_m \times \mathbf{I}_m\mathbf{\omega}_m + \mathbf{N}_{cmb}
    \right\rbrace,
$$

ここで、$(\phi_m, \theta_m, \psi_m)$は月のマントルのオイラー角、$\mathbf{\omega}_m$はマントルフレームで表現されたマントルの角速度、$\mathbf{I}_m$はマントルの慣性モーメント、$\mathbf{N}_{M,figM-pmA}$は天体$A$の点質量からの月のマントルに対するトルク、$\mathbf{N}_{M, figM - figE}$は月の拡張形状が地球の拡張形状と相互作用することによるマントルに対するトルク、$\mathbf{N}_{cmb}$はマントルとコアの相互作用によるトルクです。

$$
\textbf{月のコア}
$$

$$
\begin{align*}
    \dot{\phi}_c & = \omega_{c,z}^\dagger - \dot{\psi}_c\cos\theta_c \\
    \dot{\theta}_c & = \omega_{c,x}^\dagger \\
    \dot{\psi}_c & = -\omega_{c,y}^\dagger / \sin\theta_c
\end{align*}
$$

および

$$
    \dot{\mathbf{\omega}}_c = \mathbf{I}_c^{-1}\left\lbrace
        -\mathbf{\omega}_m \times \mathbf{I}_c\mathbf{\omega}_c - \mathbf{N}_{cmb}
    \right\rbrace,
$$

ここで、$(\phi_c, \theta_c, \psi_c)$は月のコアのオイラー角、$\mathbf{\omega}_c^\dagger$は慣性$XY$平面との交点によって定義されたフレームで表現されたコアの角速度、$\mathbf{I}_c$はコアの慣性モーメント；$\mathbf{\omega}_m$および$\mathbf{\omega}_c$はマントルフレームにおけるマントルおよびコアの角速度です；$\mathbf{N}_{cmb}$はマントルとコアの相互作用によるトルクです。 ```
