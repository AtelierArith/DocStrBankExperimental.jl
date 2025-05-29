```
regular_spherical_source(PhysicalMedium,regular_coefficients; amplitude = one(T), position = zeros(T,Dim))
```

$$
c_n =
$$

`regular_coefficients[n]`, $x_o=$`position`、$v_n(kx)$を位置$x$で波数$k$を持つ正則球基底とします。上記は`source`を返し、`source.field(x,ω) =`$\sum_n c_n v_n(kx -k x_0)$となります。
