```
function correct_network_data!(
    data::Dict{String,<:Any};
    multinetwork::Bool=false
)
```

Corrects and prepares the data in both pm and pmd dictionaries. Also, assigns the ids given in the boundary linking data to number buses. `data` is the pmitd dictionary to be corrected and `multinetwork` is the boolean that defines if there are multinetwork boundary buses to be assigned.
