```
DecreasingStepsize()
```

A functor that represents several decreasing step sizes

# Fields

  * `exponent`:   (`1`) a value $e$ the current iteration numbers $e$th exponential is taken of
  * `factor`:     (`1`) a value $f$ to multiply the initial step size with every iteration
  * `length`:     (`1`) the initial step size $l$.
  * `subtrahend`: (`0`) a value $a$ that is subtracted every iteration
  * `shift`:      (`0`) shift the denominator iterator $i$ by $s$`.
  * `type`:       a symbol that indicates whether the stepsize is relatively (:relative),   with respect to the gradient norm, or absolutely (:absolute) constant.

In total the complete formulae reads for the $i$th iterate as

$$
s_i = \frac{(l - i a)f^i}{(i+s)^e}
$$

and hence the default simplifies to just $s_i = \frac{l}{i}$

# Constructor

```
DecreasingStepsize(l=1,f=1,a=0,e=1,s=0,type=:relative)
```

Alternatively one can also use the following keyword.

```
DecreasingStepsize(
    M::AbstractManifold=DefaultManifold(3);
    length=injectivity_radius(M)/2, multiplier=1.0, subtrahend=0.0,
    exponent=1.0, shift=0, type=:relative
)
```

initializes all fields, where none of them is mandatory and the length is set to half and to $1$ if the injectivity radius is infinite.
