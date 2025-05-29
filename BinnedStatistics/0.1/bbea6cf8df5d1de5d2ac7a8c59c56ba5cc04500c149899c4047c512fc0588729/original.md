Compute a fast binned statistic for an array of y-values along some array of x-values, essentially a histogram with the chosen statistic computed at each bin.

This function is an analog to the existing scipy.stats.binned_statistic function, but written in native Julia, and this implementation is faster than the SciPy version!

Returns the bin edges, bin centers, and corresponding binned statistic. Currently implemented stats operations are sum, mean, median, variance, standard deviation, and an option to pass a custom function. The median / custom function implementation is much slower than the others (~30x slower than sum, which is the fastest), but included to match with scipy.stats.binned_statistic. It could easily be improved but left in lazy state for now.

Usage examples:

```julia
x = rand(2048,2048); y = rand(2048,2048)
edges, centers, binnedSum = binnedStatistic(x,y,nbins=500,statistic=:sum)

edges, centers, binnedSum = binnedStatistic(x,y) #defaults to :sum with 100 bins

edges, centers, binnedVar = binnedStatistic(x,y,statistic=:var) #compute the variance in each bin, leaving default of 100 bins

f(x) = sum(x.^2) #example of user defined function, must be vectorized but return a single scalar Float64 value
edges, centers, binnedF = binnedStatistic(x,y,statistic=:f,f=f)
```

This can technically be done with the existing Histogram functionality above, but it's very slow, and this new way is ~15-20x faster. Example using existing histogram routine in `StatsBase`:

```julia
function histSum(x::Array,y::Array,bins::Int=100) #compute the sum on each bin in a histogram, using the existing functionality in StatsBase
    h = fit(Histogram, vec(x), aweights(y), nbins=bins)
    h.edges, h.weights
end
```

`julia> x = rand(2048,2048); y = rand(2048,2048) julia> using BenchmarkTools julia> @btime histSum(x,y)     268.793 ms (8 allocations: 1.20 KiB)`

if using this new, faster version we obtain a ~15-20x speed-up:

`julia> @btime binnedStatistic(x,y)     14.165 ms (3 allocations: 1.83 KiB)`

These tests were performed using Julia 1.6.1 on a system running Linux Mint 20.3 Cinnamon with a Intel Core i7-1065G7 CPU (4 cores @ 1.3 GHz)
