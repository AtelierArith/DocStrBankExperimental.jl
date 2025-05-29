# Fminbox

## Constructor

```julia
Fminbox(method;
        mu0=NaN,
        mufactor=0.0001,
        precondprep(P, x, l, u, mu) -> precondprepbox!(P, x, l, u, mu))
```

## Description

Fminbox implements a primal barrier method for optimization with simple bounds (or box constraints). A description of an approach very close to the one implemented here can be found in section 19.6 of Nocedal and Wright  (sec. 19.6, 2006).

## References

  * Wright, S. J. and J. Nocedal (1999), Numerical optimization. Springer Science 35.67-68: 7.
