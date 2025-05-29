```
sysr, hs = frequency_weighted_reduction(G, Wo, Wi, r=nothing; residual=true)
```

Find Gr such that $||Wₒ(G-Gr)Wᵢ||∞$ is minimized. For a realtive reduction, set Wo = inv(G) and Wi = I.

If `residual = true`, matched static gain is achieved through "residualization", i.e., setting

$$
0 = A_{21}x_{1} + A_{22}x_{2} + B_{2}u
$$

where indices 1/2 correspond to the remaining/truncated states respectively. This choice typically results in a better match in the low-frequency region and a smaller overall error.

Ref: [Andras Varga and Brian D.O. Anderson, "Accuracy enhancing methods for the frequency-weighted balancing related model reduction"](https://elib.dlr.de/11746/1/varga_cdc01p2.pdf)

Note: This function only handles exponentially stable models. To reduce unstable  and marginally stable models, decompose the system into stable and unstable parts using [`stab_unstab`](@ref), reduce the stable part and then add the unstable part back.

# Example:

The following example performs reduction with a frequency focus between frequencies `w1` and `w2`.

```julia
using DSP
w1 = 1e-4
w2 = 1e-1
fc = DSP.analogfilter(DSP.Bandpass(w1, w2), DSP.Butterworth(2))
tfc = DSP.PolynomialRatio(fc)
W = tf(DSP.coefb(tfc), DSP.coefa(tfc))
rsys, hs = frequency_weighted_reduction(sys, W, 1)
```
