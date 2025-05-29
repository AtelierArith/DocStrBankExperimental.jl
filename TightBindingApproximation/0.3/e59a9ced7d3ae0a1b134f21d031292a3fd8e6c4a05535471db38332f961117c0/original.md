```
Fukui <: BerryCurvatureMethod
```

Fukui method to calculate Berry curvature of energy bands. see [Fukui et al, JPSJ 74, 1674 (2005)](https://journals.jps.jp/doi/10.1143/JPSJ.74.1674). Hall conductivity (single band) is given by 

$$
\sigma_{xy} = -{e^2\over h}\sum_n c_n, \nonumber \\
c_n = {1\over 2\pi}\int_{BZ}{dk_x dk_y Ω_{xy}}, 
\Omega_{xy}=(\nabla\times {\bm A})_z,
A_{x}=i\langle u_n|\partial_x|u_n\rangle.
$$
