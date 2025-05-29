```
balance_reaction(reaction::Reaction)
```

Returns a vector of all possible stoichiometrically balanced `Reaction` objects for the given `Reaction`.

Example:

```julia
t = default_t()
@species Si(t) Cl(t) H(t) O(t)
@compound SiCl4 ~ Si + 4Cl
@compound H2O ~ 2H + O
@compound H4SiO4 ~ 4H + Si + 4O
@compound HCl ~ H + Cl
rx = @reaction 1.0, SiCl4 + H2O --> H4SiO4 HCl
balance_reaction(rx) # Exactly one solution.
```

```julia
t = default_t()
@species C(t) H(t) O(t)
@compound CO ~ C + O
@compound CO2 ~ C + 2O
@compound H2 ~ 2H
@compound CH4 ~ C + 4H
@compound H2O ~ 2H + O
rx = @reaction 1.0, CO + CO2 + H2--> CH4 H2O
balance_reaction(rx) # Multiple solutions.
```

```julia
t = default_t()
@species Fe(t) S(t) O(t) H(t) N(t)
@compound FeS2 ~ Fe + 2S
@compound HNO3 ~ H + N + 3O
@compound Fe2S3O12 ~ 2Fe + 3S + 12O
@compound NO ~ N + O
@compound H2SO4 ~ 2H + S + 4O
rx = @reaction 1.0, FeS2 + HNO3 --> Fe2S3O12 NO + H2SO4
brxs = balance_reaction(rx) # No solution.
```

Notes:

  * Balancing reactions that contain compounds of compounds is currently not supported.
  * A reaction may not always yield a single solution; it could have an infinite number of solutions or none at all. When there are multiple solutions, a vector of all possible `Reaction` objects is returned. However, substrates and products may be interchanged as we currently do not solve for a linear combination that maintains the set of substrates and products.
  * If the reaction cannot be balanced, an empty `Reaction` vector is returned.
