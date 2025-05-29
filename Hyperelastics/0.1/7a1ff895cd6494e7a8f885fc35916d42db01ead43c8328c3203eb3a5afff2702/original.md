```julia
YeohFleming()
YeohFleming(type)

```

# Model:

$$
W = \frac{A}{B}(1-\exp{-B(I_1-3)}) - C_{10}(I_m-3)\log{1-\frac{I_1-3}{I_m-3}}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `A`
  * `B`
  * `C10`
  * `Im`

> Yeoh OH, Fleming PD. A new attempt to reconcile the statistical and phenomenological theories of rubber elasticity. Journal of Polymer Science Part B: Polymer Physics. 1997 Sep 15;35(12):1919-31.

