```
rand(R::QQBarField; degree::Int, bits::Int, randtype::Symbol=:null)
```

Return a random algebraic number with degree up to `degree` and coefficients up to `bits` in size. By default, both real and complex numbers are generated. Set the optional `randtype` to `:real` or `:nonreal` to generate a specific type of number. Note that nonreal numbers require `degree` at least 2.
