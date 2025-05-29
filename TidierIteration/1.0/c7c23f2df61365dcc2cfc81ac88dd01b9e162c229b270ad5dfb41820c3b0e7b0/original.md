```
flatten_dfr_json(dicts::Vector{<:Dict}, n::Int = 1)
```

Given a vector of dictionaries, flatten each of them and concatenate on a dataframe; remaining vectors and dictionaries are converted to a json string.
