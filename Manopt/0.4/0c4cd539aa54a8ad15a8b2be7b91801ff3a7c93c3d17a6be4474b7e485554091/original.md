```
NelderMeadSimplex
```

A simplex for the Nelder-Mead algorithm.

# Constructors

```
NelderMeadSimplex(M::AbstractManifold)
```

Construct a  simplex using $n+1$ random points from manifold `M`, where $n$ is the manifold dimension of `M`.

```
NelderMeadSimplex(
    M::AbstractManifold,
    p,
    B::AbstractBasis=DefaultOrthonormalBasis();
    a::Real=0.025,
    retraction_method::AbstractRetractionMethod=default_retraction_method(M, typeof(p)),
)
```

Construct a simplex from a basis `B` with one point being `p` and other points constructed by moving by `a` in each principal direction defined by basis `B` of the tangent space at point `p` using retraction `retraction_method`. This works similarly to how the initial simplex is constructed in the Euclidean Nelder-Mead algorithm, just in the tangent space at point `p`.
