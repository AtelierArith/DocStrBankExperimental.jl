```
extrap1d(itp::DataInterpolations.AbstractInterpolation; first=:extrapolate, last=:extrapolate) where {T<:Real}
```

`first` と `last` は `[:extrapolate, :flat, --value--]` であり、配列の両端での外挿の方法に影響を与えます。
