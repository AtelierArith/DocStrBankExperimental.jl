```jldoctest
julia> using ASH

julia> # Define a univariate ASH model
       model = ASH.fit(data)

julia> # Get the range of the model
       range = ASH.range(model)

julia> # Get the density of the model
       density = ASH.density(model)
```
