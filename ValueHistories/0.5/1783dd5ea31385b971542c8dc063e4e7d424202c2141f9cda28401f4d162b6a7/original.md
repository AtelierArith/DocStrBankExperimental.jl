Easily add to a MVHistory object `tr`.

Example:

```julia
using ValueHistories, OnlineStats
v = Variance(BoundedEqualWeight(30))
tr = MVHistory()
for i=1:100
    r = rand()
    fit!(v,r)
    μ,σ = mean(v),std(v)

    # add entries for :r, :μ, and :σ using their current values
    @trace tr i r μ σ
end
```
