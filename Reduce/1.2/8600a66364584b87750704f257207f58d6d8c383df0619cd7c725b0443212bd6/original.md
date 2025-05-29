```
list(r)
```

The operator `list` is an alternative to the usage of curly brackets. `list` accepts an arbitrary number of arguments and returns a list of its arguments. This operator is useful in cases where operators have to be passed as arguments. E.g.,

```Julia
julia> list(:a,list(list(:b,:c),:d),:e) == R"{{a},{{b,c},d},e}"
true
```
