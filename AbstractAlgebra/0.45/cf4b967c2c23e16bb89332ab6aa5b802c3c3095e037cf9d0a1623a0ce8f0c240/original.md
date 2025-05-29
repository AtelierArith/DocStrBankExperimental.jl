```
sqrt(a::ResFieldElem{T}; check::Bool=true) where T <: Integer
```

Return the square root of $a$. By default the function will throw an exception if the input is not square. If `check=false` this test is omitted.
