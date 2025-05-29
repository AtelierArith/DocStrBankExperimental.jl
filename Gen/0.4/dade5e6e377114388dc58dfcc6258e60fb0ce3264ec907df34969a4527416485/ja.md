```
(new_trace, accepted) = mala(
    trace, selection::Selection, tau::Real;
    check=false, observations=EmptyChoiceMap())
```

メトロポリス調整ラングビンアルゴリズム（MALA）アップデートを適用します。

[Reference URL](https://en.wikipedia.org/wiki/Metropolis-adjusted_Langevin_algorithm)
