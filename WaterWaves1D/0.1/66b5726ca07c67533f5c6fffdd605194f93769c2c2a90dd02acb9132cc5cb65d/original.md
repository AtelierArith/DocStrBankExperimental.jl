```
random(x;args)
```

Randomly generate a vector of values at collocation points `x`, based on provided (optional arguments) :

  * `L` is the typical wavelength (default is `L=1`),
  * `s` is the (real) Sobolev index regularity (default is `s=∞`, smooth data),
  * `λ` is the length of spatial localization (default is `λ=∞`, no localization),
  * `a` is the amplitude of the returned vector (default is `a=1`).

The vector is generated through randomly chosen Fourier coefficients, multiplied with weigth `w=10^(-|k|L/(2π))` if `s=∞`, or `w=1/(1+9(|k|L/(2π))^(s+1/2))` otherwise. If `λ≠∞`, the function in spatial variables is multiplied by `exp(-|x/λ|^2)`, and in any case normalized to have maximum absolute value 1.
