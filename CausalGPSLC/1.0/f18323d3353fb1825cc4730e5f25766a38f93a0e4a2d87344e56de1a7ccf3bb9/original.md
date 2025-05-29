```
extractParameters(g, posteriorSampleIdx)
```

Get inferred parameters from `g`'s `posteriorSampleIdx`*th* posterior sample.  Parameters are `uyLS, xyLS, tyLS, yNoise, yScale, U`, some of which are allowed to be `Nothing`
