```
toString(y::Rational;
         aligned::Bool=false)::String
```

where `aligned` is to be set to true whenever a numeric string is to column align with other numeric strings, such as when printing out a matrix, i.e., it prints a space whenever `y` is non-negative.
