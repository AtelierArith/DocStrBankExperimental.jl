```
HKY85(rate, pi, relative)
```

A nucleic acid substitution model based on Hasegawa et al. 1985 substitution model. `rate` should be a vector of 1 or 2 rates, and `pi` a vector of 4 probabilities summing to 1.

If `relative` is false, the 2 rates represent the transition rate and the transversion rate, α and β. If `relative` is true (default), only the first rate is used and represents the transition/transversion ratio: κ=α/β. The rate transition matrix Q is normalized to have 1 change / unit of time on average, i.e. the absolute version of Q is divided by `2(piT*piC + piA*piG)α + 2(piY*piR)β`.

`nparams` returns 1 or 2. In other words: the stationary distribution is not counted in the number of parameters (and `fitdiscrete` does not optimize the pi values at the moment).

# examples

```jldoctest
julia> m1 = HKY85([.5], [0.20, 0.30, 0.30, 0.20])
HKY85 Substitution Model base frequencies: [0.2, 0.3, 0.3, 0.2]
relative rate version with transition/tranversion ratio kappa = 0.5,
 scaled so that there is one substitution per unit time
rate matrix Q:
               A       C       G       T
       A       *  0.4839  0.2419  0.3226
       C  0.3226       *  0.4839  0.1613
       G  0.1613  0.4839       *  0.3226
       T  0.3226  0.2419  0.4839       *

julia> nstates(m1)
4

julia> m2 = HKY85([0.5, 0.5], [0.20, 0.30, 0.30, 0.20], false)
HKY85 Substitution Model base frequencies: [0.2, 0.3, 0.3, 0.2]
absolute rate version with transition/transversion ratio kappa = a/b = 1.0
 with rates a = 0.5 and b = 0.5
rate matrix Q:
               A       C       G       T
       A       *  0.1500  0.1500  0.1000
       C  0.1000       *  0.1500  0.1000
       G  0.1000  0.1500       *  0.1000
       T  0.1000  0.1500  0.1500       *

```
