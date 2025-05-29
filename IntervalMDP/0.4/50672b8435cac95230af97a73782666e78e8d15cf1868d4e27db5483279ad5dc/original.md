```
LTLfFormula
```

An LTL formula over finite traces [1]. See [`LTLFormula`](@ref) for the structure of LTL formulas. Let $ϕ$ denote the formula, $M$ denote an interval Markov process, and $H$ the time horizon. Then compute $M ⊧ ϕ$ within traces of length $H$.

### Fields

  * `formula::String`: LTL formula
  * `time_horizon::T`: Time horizon of the finite traces

[1] Giuseppe De Giacomo and Moshe Y. Vardi. 2013. Linear temporal logic and linear dynamic logic on finite traces. In Proceedings of the Twenty-Third international joint conference on Artificial Intelligence (IJCAI '13). AAAI Press, 854–860.
