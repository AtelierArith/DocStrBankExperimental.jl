```
genBasisFuncText(bf::FloatingGTBasisFuncs; 
                 norm::Real=1.0, printCenter::Bool=true, roundDigits::Int=-1) -> String
```

Generate the text of input `FloatingGTBasisFuncs`. `norm` is the additional normalization  factor. If `printCenter` is `true`, the center coordinate will be added to the first line  of the output `String`. `roundDigits` specifies the rounding digits for the parameters  inside `bf`; when set to negative, no rounding will be performed.
