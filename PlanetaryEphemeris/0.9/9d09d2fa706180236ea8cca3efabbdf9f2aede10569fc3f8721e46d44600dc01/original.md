```
NBP_pN_A_J23E_J23M_J2S_threads!(dq, q, params, t)
```

Multi-threaded Solar System (JPL DE430/431) dynamical model. Bodies considered in the model are: the Sun, the eight planets, the Moon and the 343 main-belt asteroids included in the JPL DE430 ephemeris. Effects considered are:

  * Post-Newtonian point-mass accelerations between all bodies: see equation (35) in page 7 of https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract

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

where $\mathbf{v}_i = \dot{\mathbf{r}}_i$, $\dot{s}_i = ||\mathbf{v}_i||^2$ and $\mathbf{a}_i = \ddot{\mathbf{r}}_i$.

  * Figure-effects (oblateness) of the Earth ($J_2$ and $J_3$),
  * $J_2$ effect of the Sun and
  * $J_2$ and $J_3$ effect of the Moon: see equation (28) in page 13 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract and equations (173) and (174) in page 33 of https://ui.adsabs.harvard.edu/abs/1971mfdo.book.....M/abstract

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

where $r$ is the center-of-mass separation between the two bodies; $n_1$ and $n_2$ are the maximum degrees of the zonal and tesseral expansions, respectively; $P_n(\sin\phi)$ is the Legendre polynomial of degree $n$, $P_n^m(\sin\phi)$ is the associated Legendre function of degree $n$ and order $m$, $J_n$ is the zonal harmonic coefficient for the extended body; $C_{nm}$, $S_{nm}$ are the tesseral harmonic coefficients for the extended body, $R$ is the equatorial radius of the extended body, $\phi$ is the latitude of the point mass relative to the body-fixed coordinate system in which the harmonics are expressed; and $\lambda$ is the east longitude of the point mass in the same body-fixed coordinate system. The primes denote differentiation with respect to the argument $\sin\phi$. The accelerations are transformed into the inertial frame by application of the appropriate rotation matrix.

  * Kinematic model for the precession and nutation of the Earth's orientation (IAU 1976/1980 Earth orientation model): see [`c2t_jpl_de430`](@ref).
  * Kinematic model for the Moon's orientation (Seidelmann et al., 2006): see equations (14)-(15) in page 9 and equations (34)-(35) in page 16 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

$\textbf{Lunar mantle}$

$$
\begin{align*}
    \dot{\phi}_m & = (\omega_{m,x}\sin\psi_m + \omega_{m,y}\cos\psi_m)/\sin\theta_m \\
    \dot{\theta}_m & = \omega_{m,x}\cos\psi_m - \omega_{m,y}\sin\psi_m \\
    \dot{\psi}_m & = \omega_{m,z} - \dot{\phi_m}\cos\theta_m
\end{align*}
$$

and

$$
    \dot{\mathbf{\omega}}_m = \mathbf{I}_m^{-1}\left\lbrace
        \sum_{A\neq M} \mathbf{N}_{M,fig M- pmA} + \mathbf{N}_{M,figM-figE} - \dot{\mathbf{I}}_m\mathbf{\omega}_m - \mathbf{\omega}_m \times \mathbf{I}_m\mathbf{\omega}_m + \mathbf{N}_{cmb}
    \right\rbrace,
$$

where $(\phi_m, \theta_m, \psi_m)$ are the lunar mantle Euler angles, $\mathbf{\omega}_m$ is the angular velocity of the mantle expressed in the mantle frame, $\mathbf{I}_m$ is the mantle moment of inertia, $\mathbf{N}_{M,figM-pmA}$ is the torque on the lunar mantle from the point mass of body $A$ , $\mathbf{N}_{M, figM - figE}$ is the torque on the mantle due to the extended figure of the Moon interacting with the extended figure of the Earth, and $\mathbf{N}_{cmb}$ is the torque due to interaction between the mantle and core.

$\textbf{Lunar core}$

$$
\begin{align*}
    \dot{\phi}_c & = \omega_{c,z}^\dagger - \dot{\psi}_c\cos\theta_c \\
    \dot{\theta}_c & = \omega_{c,x}^\dagger \\
    \dot{\psi}_c & = -\omega_{c,y}^\dagger / \sin\theta_c
\end{align*}
$$

and

$$
    \dot{\mathbf{\omega}}_c = \mathbf{I}_c^{-1}\left\lbrace
        -\mathbf{\omega}_m \times \mathbf{I}_c\mathbf{\omega}_c - \mathbf{N}_{cmb}
    \right\rbrace,
$$

where $(\phi_c, \theta_c, \psi_c)$ are the lunar core Euler angles, $\mathbf{\omega}_c^\dagger$ is the angular velocity of the core expressed in a frame define by the intersection of the core equator with the inertial $XY$ plane, $\mathbf{I}_c$ is the core moment of inertia; $\mathbf{\omega}_m$ and $\mathbf{\omega}_c$ are the mantle and core angular velocities in the mantle frame; and $\mathbf{N}_{cmb}$ is the torque due to interaction between the mantle and core.
