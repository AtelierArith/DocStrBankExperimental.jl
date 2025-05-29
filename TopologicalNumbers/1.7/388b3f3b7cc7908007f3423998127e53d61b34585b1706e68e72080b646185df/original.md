Fukui-Hatsugai-Suzuki method [Fukui2005Chern](@cite)

# Definition

The Berry flux at the wavenumber $\bm{k}$ of the $n$th band $F_{n}(\bm{k})$ is defined by

$$
F_{n}(\bm{k})=f_{n}(\bm{k})-df_{n}(\bm{k})
$$

$$
f_{n}(\bm{k})=\frac{1}{2\pi}\mathrm{Im}\left[\mathrm{Log}\left[U_{n,1}(\bm{k})U_{n,2}(\bm{k}+\bm{e}_{1})U_{n,1}^{*}(\bm{k}+\bm{e}_{2})U_{n,1}^{*}(\bm{k})\right]\right]
$$

$$
df_{n}(\bm{k})=\frac{1}{2\pi}\mathrm{Im}\left[\mathrm{Log}[U_{n,1}(\bm{k})]+\mathrm{Log}[U_{n,2}(\bm{k}+\bm{e}_{1})]-\mathrm{Log}[U_{n,1}(\bm{k}+\bm{e}_{2})]-\mathrm{Log}[U_{n,1}(\bm{k})]\right]
$$

$U_{n,i}(\bm{k})$ is the link variable at wavenumber $\bm{k}$. $\bm{e}_{i}$ is the unit vector.

$$
U_{n,i}(\bm{k})=\braket{\Psi_{n}(\bm{k})|\Psi_{n}(\bm{k}+\bm{e}_{i})}
$$

$\ket{\Psi_{n}(\bm{k})}$ is the wave function of the $n$th band.
