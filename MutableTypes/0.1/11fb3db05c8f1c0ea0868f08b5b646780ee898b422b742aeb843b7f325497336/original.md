```
toString(x::Complex;
         format::Char='E',
         precsion::Int=5,
         aligned::Bool=false)::String
```

where `format` ∈ {'e', 'E', 'f', 'F'} ('e' or 'E' return exponential or scientific notation, and 'f' or 'F' return fixed-point notation), while `precsion` ∈ {3, …, 7} denotes the number of significant figures. Keyword `aligned` is to be set to true whenever a numeric string is to column align with other numeric strings, such as when printing out a matrix, i.e., it prints a space whenever `y` has a non-negative real part. The returned string need not represent full precision of the actual floating-point number. Method toString is intended for printing out numbers for visual consumption.
