```
Base.sqrt(a::FracElem{T}; check::Bool=true) where T <: RingElem
```

Return the square root of $a$. By default the function will throw an exception if the input is not square. If `check=false` this test is omitted.
