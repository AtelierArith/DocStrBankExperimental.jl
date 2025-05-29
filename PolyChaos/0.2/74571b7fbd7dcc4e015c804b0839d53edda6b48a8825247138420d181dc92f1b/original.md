```
mcdiscretization(N::Int,quads::Vector{},discretemeasure::AbstractMatrix{<:Real}=zeros(0,2);discretization::Function=stieltjes,Nmax::Integer=300,ε::Float64=1e-8,gaussquad::Bool=false)
```

This routine returns $N$ recurrence coefficients of the polynomials that are orthogonal relative to a weight function $w$ that is decomposed as a sum of $m$ weights $w_i$ with domains $[a_i,b_i]$ for $i=1,\dots,m$,

$$
w(t) = \sum_{i}^{m} w_i(t) \quad \text{with } \operatorname{dom}(w_i) = [a_i, b_i].
$$

For each weight $w_i$ and its domain $[a_i, b_i]$ the function `mcdiscretization()` expects a quadrature rule of the form nodes::AbstractVector{<:Real}, weights::AbstractVector{<:Real} = my*quad*i(N::Int) all of which are stacked in the parameter `quad` quad = [ my*quad*1, ..., my*quad*m ] If the weight function has a discrete part (specified by `discretemeasure`) it is added on to the discretized continuous weight function.

The function `mcdiscretization()` performs a sequence of discretizations of the given weight $w(t)$, each discretization being followed by an application of the Stieltjes or Lanczos procedure (keyword `discretization in [stieltjes, lanczos]`) to produce approximations to the desired recurrence coefficients. The function applies to each subinterval $i$ an `N`-point quadrature rule (the $i$th entry of `quad`) to discretize the weight function $w_i$ on that subinterval. If the procedure converges to within a prescribed accuracy `ε` before `N` reaches its maximum allowed value `Nmax`. If the function does not converge, the function prompts an error message.

The keyword `gaussquad` should be set to `true` if Gauss quadrature rules are available *for all* $m$ weights $w_i(t)$ with $i = 1, \dots, m$.

For further information, please see W. Gautschi "Orthogonal Polynomials: Approximation and Computation", Section 2.2.4.
