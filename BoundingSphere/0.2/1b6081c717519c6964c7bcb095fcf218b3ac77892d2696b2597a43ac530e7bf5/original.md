```
WelzlMTF()
```

Welzl algorithm with move to front heuristic. See Algorithm I in https://people.inf.ethz.ch/gaertner/subdir/texts/own*work/esa99*final.pdf. In almost all situations it is better to use [`WelzlPivot`](@ref) instead.

## Pros

  * Fast for small examples

## Cons

  * Prone to numerical stability issues
