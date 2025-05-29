```
MultiSampler{SamplerKey,Key,Time}(which_sampler::Function)
```

This makes a sampler that uses multiple stochastic sampling algorithms (SSA) to determine the next transition to fire. It returns the soonest transition of all of the algorithms. The `which_sampler` function looks at the clock ID, or key, and chooses which sampler should sample this clock. Add algorithms to this sampler like you would add them to a dictionary.

Once a clock is first enabled, it will always go to the same sampler. This sampler remembers the associations, which could increase memory for simulations with semi-infinite clocks.

# Examples

Let's make one sampler for exponential distributions, one for a few clocks we know will be fast and one for slower clocks. We can name them with symbols. The trick is that we need to direct each kind of distribution to the correct sampler. Use a Float64 for time and each clock can be identified with an Int64.

```
using CompetingClocks
using Distributions: Exponential, UnivariateDistribution

struct ByDistribution <: SamplerChoice{Int64,Symbol} end

function CompetingClocks.choose_sampler(
    chooser::ByDistribution, clock::Int64, distribution::Exponential
    )::Symbol
    return :direct
end
function CompetingClocks.choose_sampler(
    chooser::ByDistribution, clock::Int64, distribution::UnivariateDistribution
    )::Symbol
    if clock < 100
        return :fast
    else
        return :slow
    end
end
sampler = MultiSampler{Symbol,Int64,Float64}(ByDistribution())
sampler[:direct] = OptimizedDirect{Int64,Float64}()
sampler[:fast] = FirstToFire{Int64,Float64}()
sampler[:slow] = FirstToFire{Int64,Float64}()
```
