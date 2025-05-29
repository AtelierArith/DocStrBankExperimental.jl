```
equilibrium_and_stability(UDE,X,lower,upper;t=0,Ntrials=100,tol=10^-3)
```

Attempts to find all the equilibrium points for the UDE model between the upper and lower bounds, and then returns the real component of the dominant eigenvalue to analyze stability.

...

# kwargs

  * t = 0: The point in time where the UDE model is evaluated, only relevant for time aware UDEs.
  * Ntrials = 100: the number of initializations of the root finding algorithm.
  * tol = 10^-3: The threshold Euclidean distance between points beyond which a new equilibrium is sufficiently different to be retained.

...
