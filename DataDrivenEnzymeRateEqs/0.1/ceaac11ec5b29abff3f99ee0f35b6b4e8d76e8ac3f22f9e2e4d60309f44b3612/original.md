```
derive_general_qssa_rate_eq(metabs_and_regulators_kwargs...)
```

Derive a function that calculates the rate of a reaction using the Quasi Steady State Approximation (QSSA) given the list of substrates, products, and regulators.

The general QSSA rate equation is given by:

$$
Rate = \frac{V_{max} \left(\frac{\prod_{i=1}^{n}S_i}{(K_{S1...Sn})^n}\right) - V_{max, rev} \left(\frac{\prod_{i=1}^{n}P_i}{(K_{P1...Pn})^n}\right)}{Z}
$$

where:

  * $V_{max}$ is the maximum rate of the forward reaction
  * $V_{max, rev}$ is the maximum rate of the reverse reaction
  * $S_i$, $P_i$, $R_i$ is the concentration of the $i^{th}$ substrate (S), product (P), or regulator (R)
  * $K_{X_1...X_n}$ is the kinetic constant
  * $Z$ is a combination of all terms containing products of [S], [P], and [R] divided by K*S*P_R

# Arguments

  * `metabs_and_regulators_kwargs...`: keyword arguments that specify the substrates, products, catalytic sites, regulatory sites, and other parameters of the reaction.

# Returns

  * A function that calculates the rate of the reaction using the general qssa rate equation
  * A tuple of the names of the metabolites and parameters used in the rate equation
