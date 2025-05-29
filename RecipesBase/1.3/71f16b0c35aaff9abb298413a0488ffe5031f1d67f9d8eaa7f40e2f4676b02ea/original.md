Meant to be used inside a recipe to add additional RecipeData objects to the list:

```julia
@recipe function f(::T)
    # everything get this setting
    linecolor --> :red

    @series begin
        # this setting is only for this series
        fillcolor := :green

        # return the args, just like in recipes
        rand(10)
    end

    # this is the main series... though it can be skipped by returning nothing.
    # note: a @series block returns nothing
    rand(100)
end
```
