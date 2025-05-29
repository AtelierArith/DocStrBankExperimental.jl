```
makeGlobalGrid!(tsg::TasmanianSG; type, rule, anisotropic_weights=Vector{Int32}(undef, 0), alpha=0.0, beta=0.0, custom_filename="", level_limits=Vector{Int32}(undef, 0))
```

creates a new sparse grid using a global polynomial rule discards any existing grid held by `tsg`

type: string identifying the tensor selection strategy      `level`     `curved`     `hyperbolic`     `tensor`      `iptotal`   `ipcurved`   `iphyperbolic`   `iptensor`      `qptotal`   `qpcurved`   `qphyperbolic`   `qptensor`

rule: string (defines the 1-D rule that induces the grid)

```
   Interpolation rules

      Note: the quadrature induced by those rules is constructed
            by integrating the interpolant

      `clenshaw-curtis`    `clenshaw-curtis-zero`      `fejer2`
      `rleja`    `rleja-odd`  `rleja-double2`   `rleja-double4`
      `rleja-shifted`   `rleja-shifted-even`
      `max-lebesgue`    `max-lebesgue-odd`
      `min-lebesgue`    `min-lebesgue-odd`
      `leja`            `leja-odd`
      `min-delta`       `min-delta-odd`

      `chebyshev`       `chebyshev-odd`
        approximation using roots of Chebyshev polynomials
        non-nested case (in contrast to Clenshaw-Curtis nodes)

   Quadrature rules, the weights target exactness with respect
                     to the highest polynomial degree possible

       `gauss-legendre`  `gauss-legendre-odd`
        approximation using roots of polynomials orthogonal in
        measure Uniform

       `gauss-patterson`  (a.k.a. nested Gauss-Legendre)
        Note: the nodes and weights are hard-coded hence there
        is a limit on the highest possible depth

       `gauss-chebyshev1`  `gauss-chebyshev1-odd`
       `gauss-chebyshev2`  `gauss-chebyshev2-odd`
         approximation using roots of polynomials orthogonal in
         measures  1/sqrt(1-x^2) and sqrt(1-x^2)  (respectively)

      `gauss-gegenbauer`  `gauss-gegenbauer-odd`
        approximation using roots of polynomials orthogonal in
        measure (1-x^2)^alpha

      `gauss-jacobi`
        approximation using roots of polynomials orthogonal in
        measure (1-x)^alpha * (1+x)^beta

      `gauss-laguerre`
        approximation using roots of polynomials orthogonal in
        measure x^alpha * epx(-x)

      `gauss-hermite`  `gauss-hermite-odd`
        approximation using roots of polynomials orthogonal in
        measure |x|^alpha * epx(-x^2)
```

anisotropic_weights: list or array of weights (Int)                      length must be dimension or 2*dimension                      the first dimension weights must be positive                      see the manual for details

alpha, beta: Float64       alpha : the alpha parameter for Gegenbauer, Jacobi,                Hermite and Laguerre rules       beta  : the beta parameter for Jacobi rules

custom_filename: string giving the path to the file with              custom-tabulated rule
