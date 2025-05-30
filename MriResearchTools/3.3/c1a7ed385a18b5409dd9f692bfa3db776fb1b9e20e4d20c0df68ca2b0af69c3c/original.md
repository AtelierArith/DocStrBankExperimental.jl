```
laplacianunwrap(ϕ::AbstractArray)
```

Performs laplacian unwrapping on the input phase. (1D - 4D) The phase has to be scaled to radians. The implementation is close to the original publication: Schofield and Zhu 2003, https://doi.org/10.1364/OL.28.001194. It is not the fastest implementation of laplacian unwrapping (doesn't use discrete laplacian).
