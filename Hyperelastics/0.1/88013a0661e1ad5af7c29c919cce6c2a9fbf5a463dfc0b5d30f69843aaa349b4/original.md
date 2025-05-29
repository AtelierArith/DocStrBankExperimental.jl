```julia
BahremanDarijani()
BahremanDarijani(type)

```

# Model:

$$
W = \sum\limits_{i = 1}{3}\sum\limits_{j=0}^{N} A_j (\lambda_i^{m_j}-1) + B_j(\lambda_i^{-n_j}-1)
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()`

# Parameters:

  * `A2`
  * `B2`
  * `A4`
  * `A6`

> Bahreman M, Darijani H. New polynomial strain energy function; application to rubbery circular cylinders under finite extension and torsion. Journal of Applied Polymer Science. 2015 Apr 5;132(13).

