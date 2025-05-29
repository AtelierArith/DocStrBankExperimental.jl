```
𝒮_plus(tpt)
```

The set of indices `i` such that

  * if `i` is in `B_true`, then `i` is in `S_plus`
  * if `i` is outside `B_true`, then `i` is in `S_plus` if both 

      * `q_minus[i] > 0.0`
      * `sum(P[i, j]*qp[j] for j in sets.S) > 0.0`

Intuitively: `i` is either in `B_true`, or could have come from `A_true` and is connected to a state that is reactively connected to `B`.
