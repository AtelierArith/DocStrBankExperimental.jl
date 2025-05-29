```
seed!(tuple_obj::TupleSpace, seeds...)
```

Manually set the seed to the assigned values.

# Example

julia> space = TupleSpace([Discrete(5), Discrete(10)]) . . .

julia> seed!(space, 42, 87) # Since there are only two spaces in the TupleSpace

julia> sample(space) (4, 5)
