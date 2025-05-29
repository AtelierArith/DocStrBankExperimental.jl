```
cat_expand(cat_array::CategoricalArray, new_levels...; after=Inf)
```

Expands the levels in a categorical array by adding new levels at a specified position.

# Arguments

  * `cat_array`: Categorical array to expand levels
  * `new_levels`: New levels to be added to the categorical array
  * `after`: Position after which to insert the new levels. Default is Inf, which appends the new levels at the end.

# Returns

Categorical array with the new levels added.

# Examples

```julia
julia> cats = CategoricalArray(["a", "b", "c", "a", "c", "b"]);

julia> println("Original levels: ", levels(cats))
Original levels: ["a", "b", "c"]

julia> cats = cat_expand(f, "d", "e", "f");

julia> println("Expanded levels: ", levels(cats))
Expanded levels: ["a", "b", "c", "d", "e", "f"]
```
