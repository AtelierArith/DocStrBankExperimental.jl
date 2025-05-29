Shiozaki method [Shiozaki2023discrete](@cite)

# Definition

The $\mathbb{Z}_{2}$ number of the $2n$th (and $2n-1$th) band $\nu_{n}$ is defined by

$$
\nu_{n}=F_{n}-\left(P_{n}(0)-P_{n}(\pi)\right)
$$

$F_{n}$ is the Berry flux of the $n$th band in the $\mathrm{BZ}'$. The range $\mathrm{BZ}'$ is $\bm{k}\in[0,2\pi]\times[0,\pi]$ half of BZ(Brillouin Zone).

$$
F_{n}=\frac{1}{2\pi}\sum_{\bm{k}\in\mathrm{BZ}'}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,1}^{*}(\bm{k})\right]\right]
$$

$P_{n}(k_{2})$ is the time-reversal polarization at wavenumber $k_{2}$.

$$
P_{n}(k_{2})=\frac{1}{2\pi}\frac{\mathrm{Pf}[\omega(0,k_{2})]}{\mathrm{Pf}[\omega(\pi,k_{2})]}\sum_{k_{1}=0}^{\pi-e_{1}}U_{n,1}(\bm{k})
$$

$U_{n,i}(\bm{k})$ is the link variable at wavenumber $\bm{k}$. $\bm{e}_{i}$ is the unit vector.

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$\ket{\Psi_{n}(\bm{k})}$ is the wave function of the $2n$th (and $2n-1$th) band. $\omega(\bm{k})$ is the unitary matrix given by

$$
\omega(\bm{k})=\bra{\Psi(-\bm{k})}T\ket{\Psi(\bm{k})}
$$

$T$ is the time-reversal operator.
