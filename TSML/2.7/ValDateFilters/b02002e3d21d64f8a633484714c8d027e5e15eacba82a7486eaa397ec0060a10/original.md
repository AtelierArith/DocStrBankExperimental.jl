```
Matrifier(Dict(
   Dict(
    :ahead  => 1,
    :size   => 7,
    :stride => 1,
  )
)
```

Converts a 1-D timeseries into sliding window matrix for ML training:

  * `:ahead`  => steps ahead to predict
  * `:size`   => size of sliding window
  * `:stride` => amount of overlap in sliding window

Example:

```
mtr = Matrifier(Dict(:ahead=>24,:size=>24,:stride=>5))
lower = DateTime(2017,1,1)
upper = DateTime(2017,1,5)
dat=lower:Dates.Hour(1):upper |> collect
vals = 1:length(dat)
x = DataFrame(Date=dat,Value=vals)
fit!(mtr,x)
res = transform!(mtr,x)
```

Implements: `fit!`, `transform`
