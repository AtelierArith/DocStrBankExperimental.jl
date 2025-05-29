```
initialize_input(::Subsystem{T})
```

generate the neutral element for inputs to a given `Subsystem` such that

```julia
acc = initialize_input(sys)
combine(acc, another_input) == another_input
```

If `combine` just adds together inputs, then `initalize_input` should be zero or a collection of zeros.
