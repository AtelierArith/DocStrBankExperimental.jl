```
(new_trace, accepted) = mala(
    trace, selection::Selection, tau::Real;
    check=false, observations=EmptyChoiceMap())
```

Apply a Metropolis-Adjusted Langevin Algorithm (MALA) update.

[Reference URL](https://en.wikipedia.org/wiki/Metropolis-adjusted_Langevin_algorithm)
