```
 H = freqresp(sys, ω)
```

Compute the frequency response `H` of the descriptor system `sys = (A-λE,B,C,D)` at the real frequencies `ω`. 

For a system with `p` outputs and `m` inputs, and for `N` frequency values in `ω`, `H` is a `p × m × N` array, where `H[:,:,i]` contains the `i`-th value of the frequency response computed as `C*((w[i]*E - A)^-1)*B + D`, where `w[i] = im*ω[i]` for a continuous-time system and `w[i] = exp(im*ω[i]*|Ts|)`  for a discrete-time system with sampling time `Ts`. 

*Method:* For an efficient evaluation of `C*((w[i]*E - A)^-1)*B + D` for many values of `w[i]`, a preliminary  orthogonal coordinate transformation is performed such that for the input-output equivalent transformed  system `sys = (At-λEt,Bt,Ct,Dt)`, the matrix `w[i]*Et - At` is upper Hessenberg.  This allows an efficient computation of the frequency response using the Hessenberg-form based  approach proposed in [1].

*Reference:*

[1] Laub, A.J., "Efficient Multivariable Frequency Response Computations",     IEEE Transactions on Automatic Control, AC-26 (1981), pp. 407-408.
