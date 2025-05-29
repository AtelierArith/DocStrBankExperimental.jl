```
wrap_gsl_matrix(m::Ptr{gsl_matrix}) -> Array{Float64,2}
```

gsl_matrixのデータをラップするJulia行列を返します

**忘れないでください** GSLは行列を行優先で格納するため、行列は転置されます。
