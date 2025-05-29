```
Normalizer(Dict(
   :method => :zscore
))
```

Transforms continuous features into normalized form such as zscore, unitrange, square-root, log, pca, ppca with parameter: 

  * `:method` => `:zscore` or `:unitrange` or `:sqrt` or `:log` or `pca` or `ppca` or `fa`
  * `:zscore` => standard z-score with centering and scaling
  * `:unitrange` => unit range normalization with centering and scaling
  * `:sqrt` => square-root transform
  * `:pca` => principal component analysis transform
  * `:ppca` => probabilistic pca
  * `:fa` => factor analysis
  * `:log` => log transform

Example:

```
function generatedf()
    Random.seed!(123)
    gdate = DateTime(2014,1,1):Dates.Minute(15):DateTime(2016,1,1)
    gval1 = rand(length(gdate))
    gval2 = rand(length(gdate))
    gval3 = rand(length(gdate))
    X = DataFrame(Date=gdate,Value1=gval1,Value2=gval2,Value3=gval3)
    X
end

X = generatedf()
norm = Normalizer(Dict(:method => :zscore))
fit!(norm,X)
res=transform!(norm,X)
```

Implements: `fit!`, `transform!`
