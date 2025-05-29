```
derive_general_mwc_rate_eq(metabs_and_regulators_kwargs...)
```

Derive a function that calculates the rate of a reaction using the general MWC rate equation given the list of substrates, products, and regulators that bind to specific cat or reg sites.

The general MWC rate equation is given by:

$$
Rate = \frac{{V_{max}^a \prod_{i=1}^{n} \left(\frac{S_i}{K_{a, i}}\right) - V_{max, rev}^a \prod_{i=1}^{n} \left(\frac{P_i}{K_{a, i}}\right) \cdot Z_{a, cat}^{n-1} \cdot Z_{a, reg}^n + L \left(V_{max}^i \prod_{i=1}^{n} \left(\frac{S_i}{K_{i, i}}\right) - V_{max, rev}^i \prod_{i=1}^{n} \left(\frac{P_i}{K_{i, i}}\right)\right) \cdot Z_{i, cat}^{n-1} \cdot Z_{i, reg}^n}}{Z_{a, cat}^n \cdot Z_{a, reg}^n + L \cdot Z_{i, cat}^n \cdot Z_{i, reg}^n}
$$

where:

  * $V_{max}^a$ is the maximum rate of the forward reaction
  * $V_{max, rev}^a$ is the maximum rate of the reverse reaction
  * $V_{max}^i$ is the maximum rate of the forward reaction
  * $V_{max, rev}^i$ is the maximum rate of the reverse reaction
  * $S_i$ is the concentration of the $i^{th}$ substrate
  * $P_i$ is the concentration of the $i^{th}$ product
  * $I_i$ is the concentration of the $i^{th}$ catalytic site inhibitor
  * $R_i$ is the concentration of the $i^{th}$ allosteric regulator
  * $K_{a, X}$ is the binding constant of the $X$ metabolite for active MWC state
  * $K_{i, X}$ is the binding constant of the $X$ metabolite for inactive MWC state
  * $Z_{a, cat}$ is the allosteric factor for the catalytic site in the active MWC state
  * $Z_{i, cat}$ is the allosteric factor for the catalytic site in the inactive MWC state
  * $Z_{a, reg}$ is the allosteric factor for the regulatory site in the active MWC state
  * $Z_{i, reg}$ is the allosteric factor for the regulatory site in the inactive MWC state
  * $L$ is the ratio of inactive to active enzyme conformations in the absence of ligands
  * $n$ is the oligomeric state of the enzyme

# Arguments

  * `metabs_and_regulators_kwargs...`: keyword arguments that specify the substrates, products, catalytic sites, regulatory sites, and other parameters of the reaction.

# Returns

  * A function that calculates the rate of the reaction using the general MWC rate equation
  * A tuple of the names of the metabolites and parameters used in the rate equation
