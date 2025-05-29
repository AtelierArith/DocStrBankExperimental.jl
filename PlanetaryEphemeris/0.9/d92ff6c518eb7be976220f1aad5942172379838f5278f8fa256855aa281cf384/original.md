```
DE430!(dq, q, params, t)
```

Solar System (JPL DE430/431) dynamical model. This function uses threads and includes all the effects in `NBP_pN_A_J23E_J23M_J2S_threads!` plus

  * Tidal secular acceleration of Moon due to rides raised on Earth by both the Moon and the Sun: see equation (32) in page 14 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract

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

where $k_{2j,E}$ with $j = 0, 1, 2$ are the degree-2 Love numbers corresponding to tides with long-period, diurnal, and semi-diurnal periods, respectively; $m_E$, $m_M$ and $m_T$ are the masses of the Earth, the Moon and the tide-raising body, respectively; $R_E$ is the Earth's radius; the position vectors $\mathbf{r}$ and $\mathbf{r}_j^*$ with $j = 0, 1, 2$ are expressed in cylindrical coordinates with the $Z$ axis perpendicular to the Earth’s equator, so that $\mathbf{r} = \mathbf{\rho} + \mathbf{z}$ and the time-delayed position of the tide-raising body is given by $\mathbf{r}_j^* = \mathbf{\rho}_j^* + \mathbf{z}_j^*$; and $\mathbf{a}_{M,tide}$ is the acceleration of the Moon with respect to Earth, for each tide-raising body.

See also [`NBP_pN_A_J23E_J23M_J2S_threads!`](@ref).
