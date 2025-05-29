```
exactconv(I, x::F) :: Union{I,Nothing}
exactconv(F, x::I) :: Union{F,Nothing}
```

Convert between integer and floating-point types. The conversion suceeds only if it does not change the numeric value, otherwise it returns `nothing`.
