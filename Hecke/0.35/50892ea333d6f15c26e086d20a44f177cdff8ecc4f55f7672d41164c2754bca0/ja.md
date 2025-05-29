```
lattice_with_local_conditions(O::AlgAssAbsOrd,
                              ps::Vector{<: IntegerUnion},
                              Is::Vector{<: AlgAssAbsOrdIdl})
                                                          -> AlgAssAbsOrdIdl
```

与えられた順序 $\mathcal{O}$、素数のリスト `ps`、および格子のリスト `Is` に対して、次の条件を満たす格子 $M$ を返します。すなわち、素数 $p$ および与えられたリストの格子 $I$ に対して $M_{p} = I_p$ であり、`ps` の外の素数に対して $M_q = \mathcal{O}_q$ です。
