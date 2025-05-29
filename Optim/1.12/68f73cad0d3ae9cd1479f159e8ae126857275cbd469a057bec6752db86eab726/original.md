# Conjugate Gradient Descent

## Constructor

```julia
ConjugateGradient(; alphaguess = LineSearches.InitialHagerZhang(),
linesearch = LineSearches.HagerZhang(),
eta = 0.4,
P = nothing,
precondprep = Returns(nothing),
manifold = Flat())
```

The strictly positive constant $eta$ is used in determining the next step direction, and the default here deviates from the one used in the original paper (where it was $0.01$). See more details in the original papers referenced below.

## Description

The `ConjugateGradient` method implements Hager and Zhang (2006) and elements from Hager and Zhang (2013). Notice, the default `linesearch` is `HagerZhang` from LineSearches.jl. This line search is exactly the one proposed in Hager and Zhang (2006).

## References

  * W. W. Hager and H. Zhang (2006) Algorithm 851: CG_DESCENT, a conjugate gradient method with guaranteed descent. ACM Transactions on Mathematical Software 32: 113-137.
  * W. W. Hager and H. Zhang (2013), The Limited Memory Conjugate Gradient Method. SIAM Journal on Optimization, 23, pp. 2150-2168.
