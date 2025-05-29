```
WilksTest(DM::DataModel, θ::AbstractVector{<:Number}, Confvol=ConfVol(1)) -> Bool
```

Checks whether a given parameter configuration `θ` is within a confidence interval of level `Confvol` using Wilks' theorem. This makes the assumption, that the likelihood has the form of a normal distribution, which is asymptotically correct in the limit that the number of datapoints is infinite. The keyword `dof` can be used to manually specify the degrees of freedom.
