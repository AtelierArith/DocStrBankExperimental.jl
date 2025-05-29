```
bseries(f::Function, order, iterator_type=RootedTreeIterator)
```

Return a truncated B-series up to the specified `order` with coefficients determined by `f`. The type of rooted trees is determined by the `iterator_type`, which can be `RootedTreeIterator` or `BicoloredRootedTreeIterator`. Calling `f(t, series)` needs to return the coefficient of the rooted tree `t` of the desired series in a type-stable manner. For the empty tree, `f` is called as `f(t, nothing)`. Otherwise, the series constructed so far is passed as second argument, allowing one to access values of lower-order trees.

!!! note "Normalization by elementary differentials"
    The coefficients of the B-series returned by this method need to be multiplied by a power of the time step divided by the `symmetry` of the rooted tree and multiplied by the corresponding elementary differential of the input vector field $f$. See also [`evaluate`](@ref).


# Examples

The B-series of the average vector field (AVF) method is given by $b(.) = 1$ and $b([t_1, ..., t_n]) = b(t_1)...b(t_n) / (n + 1)$, see

  * Elena Celledoni, Robert I. McLachlan, David I. McLaren, Brynjulf Owren, G. Reinout W. Quispel, and William M. Wright. "Energy-preserving Runge-Kutta methods." ESAIM: Mathematical Modelling and Numerical Analysis 43, no. 4 (2009): 645-649. [DOI: 10.1051/m2an/2009020](https://doi.org/10.1051/m2an/2009020)

We can generate this as follows.

```jldoctest
julia> series = bseries(3) do t, series
           if order(t) in (0, 1)
               return 1 // 1
           else
               v = 1 // 1
               n = 0
               for subtree in SubtreeIterator(t)
                   v *= series[subtree]
                   n += 1
               end
               return v / (n + 1)
           end
       end
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 5 entries:
  RootedTree{Int64}: Int64[]   => 1
  RootedTree{Int64}: [1]       => 1
  RootedTree{Int64}: [1, 2]    => 1//2
  RootedTree{Int64}: [1, 2, 3] => 1//4
  RootedTree{Int64}: [1, 2, 2] => 1//3
```
