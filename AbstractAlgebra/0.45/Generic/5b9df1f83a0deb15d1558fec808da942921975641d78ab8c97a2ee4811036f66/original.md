```
sqrt(a::Generic.PuiseuxSeriesElem{T}; check::Bool=true) where T <: RingElement
```

Return the square root of the given Puiseux series $a$. By default the function will throw an exception if the input is not square. If `check=false` this test is omitted.
