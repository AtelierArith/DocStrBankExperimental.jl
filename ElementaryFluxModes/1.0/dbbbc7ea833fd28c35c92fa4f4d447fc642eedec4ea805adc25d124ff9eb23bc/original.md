```julia
DDBinary(N, K) -> Any

```

Implement the Double Description method in binary form. The input variables are: -`N`: the stoichiometric matrix with only forward reactions. If any fluxes are fixed then N has the form [N1 w] where N1 is the stoichiometric matrix for non-fixed fluxes, and w is the columns of fixed fluxes multiplied by their flux values. -`K`: initial nullspace of N, in the form [I;K*] Output: -`R`: binary elementary flux modes
