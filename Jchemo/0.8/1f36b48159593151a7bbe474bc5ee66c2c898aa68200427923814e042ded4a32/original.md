```
mweightcla(y::AbstractVector; prior::Union{Symbol, Vector} = :prop)
mweightcla(Q::DataType, y::Vector; prior::Union{Symbol, Vector} = :prop)
```

Compute observation weights for a categorical variable, given specified sub-total weights      for the classes.

  * `y` : A categorical variable (n) (class membership).
  * `Q` : A data type (e.g. `Float32`).

Keyword arguments:

  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).

Return an object of type `Weight` (see function `mweight`) containing a vector `w` (n) that sums to 1.

## Examples

```julia
using Jchemo

y = vcat(rand(["a" ; "c"], 900), repeat(["b"], 100))
tab(y)
weights = mweightcla(y)
#weights = mweightcla(y; prior = :prop)
#weights = mweightcla(y; prior = [.1, .7, .2])
res = aggstat(weights.w, y; algo = sum)
[res.lev res.X]
```
