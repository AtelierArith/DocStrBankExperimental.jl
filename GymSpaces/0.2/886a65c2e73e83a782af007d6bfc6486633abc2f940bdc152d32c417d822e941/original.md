```
seed!(dict_obj::DictSpace; kwarg_seeds...)
```

Seeds the spaces in the DictSpace. Currently, seeding of DictSpaces with only Symbol keys is allowed.

# Example

julia> space = DictSpace(Dict(:position => Discrete(5),                               :velocity => Box([0, 0], [1, 5], Float32))) . . .

julia> seed!(space, position=42)

julia> seed!(space, position=2, velocity=4)
