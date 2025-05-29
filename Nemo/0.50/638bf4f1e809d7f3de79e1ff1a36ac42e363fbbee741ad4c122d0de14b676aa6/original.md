```
accuracy_bits(x::ArbFieldElem)
```

Return the relative accuracy of $x$ measured in bits, capped between `typemax(Int)` and `-typemax(Int)`.
