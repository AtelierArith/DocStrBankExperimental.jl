```
extrap1d(itp::DataInterpolations.AbstractInterpolation; first=:extrapolate, last=:extrapolate) where {T<:Real}
```

`first` and `last` can be `[:extrapolate, :flat, --value--]` affect how the extrapolation is done at the either end of the array
