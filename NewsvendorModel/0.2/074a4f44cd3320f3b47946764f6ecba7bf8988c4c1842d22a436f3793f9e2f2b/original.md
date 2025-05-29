```
NVModel(demand, cost, price, salvage=0)
```

Captures a [Newsvendor model](https://en.wikipedia.org/wiki/Newsvendor_model)  with unit `cost`, unit selling `price`, and  `demand` distribution. The demand can be any univariate distribution from the  package [Distributions.jl](https://juliastats.org/Distributions.jl/latest/univariate/).

# Examples

```julia-repl
julia> using Distributions
```

```jldoctest nvm; setup = :(using Distributions, NewsvendorModel)
julia> nvm = NVModel(demand = Normal(50, 20), cost = 5, price = 7)
Data of the Newsvendor Model
 * Demand distribution: Normal{Float64}(μ=50.0, σ=20.0)
 * Unit cost: 5.00
 * Unit selling price: 7.00
```

This defines a model with unit cost 5 and unit price 7, where uncertain demand  draws from a normal distribution with mean 50 and standard deviation 20.

Optional keyword arguments and their defaults:

```
NVModel(demand [; kwargs])
```

  * `cost` for a unit; defaults to `0.0`
  * `price` for selling a unit; defaults to `0.0`
  * `salvage` value obtained from scraping a leftover unit; defaults to `0.0`
  * `holding` cost induced by a leftover unit, e.g., extra captial cost or warehousing cost; essentially a negative salvage value; defaults to `0.0`
  * `backorder` penalty for being short a unit, e.g., contractual penalty for missing delivery targets or missed future profit of an unserved customer; defaults to `0.0`
  * `substitute` benefit received from selling an alternative to an unserved customer, e.g., when selling another product or serving in the future; essentially a negative backorder penalty; defaults to `0.0`
  * `fixcost` fixed cost of operations; defaults to `0.0`
  * `q_min` minimal feasible quantity, e.g., due to production limits; must be nonnegative; defaults to `0`
  * `q_max` maximal feasible quantity, e.g., due to production limits; must be greater than or equal to `q_min`; defaults to `Inf`

# Examples

Define a newsvendor problem with unit cost 5, unit price 7, uniform demand between 50 and 80, where a unit salvages for 0.5, and backorder comes at a penalty  of 2 per unit, and the operations incur a fixed cost of 100, as follows:

```jldoctest nvm
julia> nvm2 = NVModel(demand = Uniform(50, 80), cost = 5, price = 7, salvage = 0.5, backorder = 2, fixcost = 100)
Data of the Newsvendor Model
 * Demand distribution: Uniform{Float64}(a=50.0, b=80.0)
 * Unit cost: 5.00
 * Unit selling price: 7.00
 * Unit salvage value: 0.50
 * Unit backorder penalty: 2.00
 * Fixed cost: 100.00
```

Note that demand is a necessary argument that can be passed without keyword in first place. Moreover, only values that differ from the default will be shown.

Define a newsvendor problem with unit cost 5, unit price 7, uniform demand between 50 and 80, where a unit salvages for 0.5, and backorder comes at a penalty  of 2 per unit, and the operations incur a fixed cost of 100, as follows:

```jldoctest nvm
julia> nvm3 = NVModel(Uniform(50, 80), 5, 7, 0.5, backorder = 2, fixcost = 100, q_min=0)
Data of the Newsvendor Model
 * Demand distribution: Uniform{Float64}(a=50.0, b=80.0)
 * Unit cost: 5.00
 * Unit selling price: 7.00
 * Unit salvage value: 0.50
 * Unit backorder penalty: 2.00
 * Fixed cost: 100.00
julia> nvm3 == nvm2
true
```

Holding cost is essentially overage cost. Backorder penalty is essentially underage cost. The beer game has holding cost of 0.5 USD and backlog costs 1 USD per unit.  Demand is assumed to be uniform betwen 0 and 300. 

```jldoctest nvm
julia> beer = NVModel(Uniform(0, 300), backorder = 1, holding = 0.5)
Data of the Newsvendor Model
 * Demand distribution: Uniform{Float64}(a=0.0, b=300.0)
 * Unit cost: 0.00
 * Unit selling price: 0.00
 * Unit holding cost: 0.50
 * Unit backorder penalty: 1.00
```
