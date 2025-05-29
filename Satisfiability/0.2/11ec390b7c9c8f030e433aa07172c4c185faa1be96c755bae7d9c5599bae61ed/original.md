```
output = "(
(define-fun x () Bool true)
(define-fun y () Bool false)
(define-fun f ((x!0 Bool)) Bool (ite (= x!0 false) true false))"
dict = parse_model(output)
```

Parse the SMT-LIB-formatted output of `(get-model)`, returning a Dict of names and values. Values will be of the correct type; thus, in the example `dict["x"]` will be `true`. Uninterpreted function values will be Julia functions themselves, thus `dict["f"]` is a function that accepts a Bool and returns a Bool.

This function is primarily useful when working with `InteractiveSolver`s.
