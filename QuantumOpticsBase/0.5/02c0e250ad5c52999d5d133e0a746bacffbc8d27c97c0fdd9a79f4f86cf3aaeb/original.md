```
transition([T=ComplexF64,] mb::ManyBodyBasis, to, from)
```

Operator $|\mathrm{to}⟩⟨\mathrm{from}|$ transferring particles between modes.

Note that `to` and `from` can be collections of indices. The resulting operator in this case will be equal to $\ldots a^\dagger_{to_2} a^\dagger_{to_1} \ldots a_{from_2} a_{from_1}$.
