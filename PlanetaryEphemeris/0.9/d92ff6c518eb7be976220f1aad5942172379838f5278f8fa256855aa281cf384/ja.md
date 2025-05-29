```
DE430!(dq, q, params, t)
```

太陽系 (JPL DE430/431) 動力学モデル。この関数はスレッドを使用し、`NBP_pN_A_J23E_J23M_J2S_threads!` に含まれるすべての効果に加えて、以下を含みます。

  * 月に対する潮汐の長期加速度：月と太陽によって地球に引き起こされる潮汐の影響： https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract の14ページの式 (32) を参照してください。

$$
\begin{align*}
    \mathbf{a}_{M,tide} & = \frac{3}{2}\left(\frac{m_E + m_M}{m_E}\right)\frac{Gm_T R_E^5}{r^5}
    \left\lbrace
        \frac{k_{20,E}}{r_0^*\,^5}\left(\left[2z_0^*\,^2\mathbf{z} + \rho_0^*\,^2\mathbf{\rho}\right]
        - \frac{5\left[\left(zz_0^*\right)^2 + \frac{1}{2}\left(\rho\rho_0^*\right)^2\right]\mathbf{r}}{r^2}
        + r_0^*\,^2\mathbf{r} \right) \right. \\
        & \hspace{0.5cm} + \frac{k_{21,E}}{r_1^*\,^5}\left(2\left[\left(\mathbf{\rho}\cdot\mathbf{\rho}_1^*\right)\mathbf{z}_1^*
        + zz_1^*\mathbf{\rho}_1^*\right]
        - \frac{10zz_1^*\left(\mathbf{\rho}\cdot\mathbf{\rho}_1^*\right)\mathbf{r}}{r^2}\right) \\
        & \hspace{0.5cm} + \left. \frac{k_{22,E}}{r_2^*\,^5}\left(
        \left[2\left(\mathbf{\rho}\cdot\mathbf{\rho}_2^*\right)\mathbf{\rho}_2^* - \rho_2^*\,^2\mathbf{\rho}\right]
        - \frac{5\left[\left(\mathbf{\rho}\cdot\mathbf{\rho}_2^*\right)^2 - \frac{1}{2}\left(\rho\rho_2^*\right)^2\right]\mathbf{r}}{r^2}
        \right)
    \right\rbrace,
\end{align*}
$$

ここで、$k_{2j,E}$ は $j = 0, 1, 2$ の潮汐に対応する2次のラブ数であり、長周期、日周、半日周の潮汐にそれぞれ対応します。$m_E$, $m_M$ および $m_T$ はそれぞれ地球、月、潮汐を引き起こす天体の質量です。$R_E$ は地球の半径です。位置ベクトル $\mathbf{r}$ および $\mathbf{r}_j^*$ ($j = 0, 1, 2$) は、$Z$ 軸が地球の赤道に垂直な円筒座標で表され、$\mathbf{r} = \mathbf{\rho} + \mathbf{z}$ となり、潮汐を引き起こす天体の時間遅延位置は $\mathbf{r}_j^* = \mathbf{\rho}_j^* + \mathbf{z}_j^*$ で与えられます。そして、$\mathbf{a}_{M,tide}$ は、各潮汐を引き起こす天体に対する月の加速度です。

また、[`NBP_pN_A_J23E_J23M_J2S_threads!`](@ref) も参照してください。
