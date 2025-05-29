```
N = remezord(Wp, Ws, Rp, Rs)
```

Order estimation for lowpass digital filter cases based on the equations and coefficients in [^Rabiner]. The original equation returned the minimum filterlength, whereas this implementation  returns the order (N=L-1). `Wp` and  `Ws` are the normalized passband and  stopband frequencies, with `Rp` indicating the passband ripple and `Rs` is the  stopband attenuation (linear.) 

NOTE: The value of N is an initial approximation. If under-estimated, the order should be increased until the design specifications are met.

[^Rabiner]: Herrmann, O., Lawrence R. Rabiner, and D. S. K. Chan. "Practical

design rules for optimum finite impulse response lowpass digital filters." Bell System  Technical Journal 52.6 (1973): 769-799.
