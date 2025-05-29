```
Dateifier(args=Dict())
   Dict(
    :ahead => 1,
    :size => 7,
    :stride => 1
   )
)
```

Converts a 1-D date series into sliding window matrix for ML training

Example: 

```
dtr = Dateifier(Dict())
lower = DateTime(2017,1,1)
upper = DateTime(2018,1,31)
dat=lower:Dates.Day(1):upper |> collect
vals = rand(length(dat))
x=DataFrame(Date=dat,Value=vals)
fit!(dtr,x)
res = transform!(dtr,x)
```

Implements: `'fit!`, `transform!`
