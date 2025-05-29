```
register_informat(f)
```

Register function `f` as an informat for using in `filereader`.

> The `filereader` function uses the latest definition of `f`, however, user must re-register the function `f` whenever it is modified to avoid allocation.


# Examples

```jldoctest
julia> function new_infmt!(x)
            replace!(x, "Y"=>"1")
        end
new_infmt! (generic function with 1 method)

julia> register_informat(new_infmt!)
[ Info: Informat new_infmt! has been registered

```
