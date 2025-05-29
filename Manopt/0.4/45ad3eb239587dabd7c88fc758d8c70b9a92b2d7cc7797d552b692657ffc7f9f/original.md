```
ConstantStepsize <: Stepsize
```

A functor that always returns a fixed step size.

# Fields

  * `length`: constant value for the step size
  * `type`:   a symbol that indicates whether the stepsize is relatively (:relative),   with respect to the gradient norm, or absolutely (:absolute) constant.

# Constructors

```
ConstantStepsize(s::Real, t::Symbol=:relative)
```

initialize the stepsize to a constant `s` of type `t`.

```
ConstantStepsize(M::AbstractManifold=DefaultManifold(2);
    stepsize=injectivity_radius(M)/2, type::Symbol=:relative
)
```

initialize the stepsize to a constant `stepsize`, which by default is half the injectivity radius, unless the radius is infinity, then the default step size is `1`.
