```julia
eachmatrix(
    L::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray
) -> Any

```

Iterator for the non-horizontal dimensions in LowerTriangularArrays. To be used like

```
for k in eachmatrix(L)
    L[1, k]
```

to loop over every non-horizontal dimension of L.
