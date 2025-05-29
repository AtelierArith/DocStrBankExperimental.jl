```julia
ExpLn()
ExpLn(type)

```

# Model:

$$
W = A\bigg[\frac{1}{a}\exp{(a(I_1-3))}+b(I_1-2)(1-\log{I_1-2})-\frac{1}{a}-b\bigg]
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `A`
  * `a`
  * `b`

> Khajehsaeid H, Arghavani J, Naghdabadi R. A hyperelastic constitutive model for rubber-like materials. European Journal of Mechanics-A/Solids. 2013 Mar 1;38:144-51.

