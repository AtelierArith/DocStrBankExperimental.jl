```
regular_spherical_source(PhysicalMedium,regular_coefficients; amplitude = one(T), position = zeros(T,Dim))
```

$c_n =$`regular_coefficients[n]`, $x_o=$`position`, and let $v_n(kx)$ represent the regular spherical basis with wavenumber $k$ at position $x$. The above returns a `source` where `source.field(x,ω) =`$\sum_n c_n v_n(kx -k x_0)$
