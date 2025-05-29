You can easily define your own plotting recipes with convenience methods:

```julia
@userplot GroupHist

@recipe function f(gh::GroupHist)
    # set some attributes, add some series, using gh.args as input
end
# now you can plot like:
grouphist(rand(1_000, 4))
```
