```
observation(m::POMDP, statep)
observation(m::POMDP, action, statep)
observation(m::POMDP, state, action, statep)
```

Return the observation distribution. You need only define the method with the fewest arguments needed to determine the observation distribution.

If it is difficult to define the probability density or mass function explicitly, consider using `POMDPModelTools.ImplicitDistribution` to define a generative model.

# Example

```julia
using POMDPModelTools # for SparseCat

struct MyPOMDP <: POMDP{Int, Int, Int} end

observation(p::MyPOMDP, sp::Int) = SparseCat([sp-1, sp, sp+1], [0.1, 0.8, 0.1])
```
