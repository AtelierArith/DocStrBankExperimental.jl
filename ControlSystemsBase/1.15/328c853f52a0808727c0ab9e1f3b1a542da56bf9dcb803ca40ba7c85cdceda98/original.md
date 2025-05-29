```
thiran(τ::Real, Ts)
```

Discretize a potentially fractional delay $τ$ as a Thiran all-pass filter with sample time `Ts`. 

The Thiran all-pass filter gives an a maximally flat group delay.

If $τ$ is an integer multiple of $Ts$, the Thiran all-pass filter reduces to $z^{-τ/Ts}$.

Ref: T. I. Laakso, V. Valimaki, M. Karjalainen and U. K. Laine, "Splitting the unit delay [FIR/all pass filters design]," in IEEE Signal Processing Magazine, vol. 13, no. 1, 1996.
