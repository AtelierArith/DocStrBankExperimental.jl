ifftav(F::AutoVector{ComplexF64},freqspacing,maxind)

For a function F_i defined on a uniform frequency grid with spacing freqspacing,  returns the Inverse Fourier Transform.

$f(x) = \frac{1}{\sqrt{2 \pi}} \int dk e^{i k x} F(k)$
