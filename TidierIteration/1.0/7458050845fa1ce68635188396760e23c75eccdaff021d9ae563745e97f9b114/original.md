```
flatten_dict(key, value:: Dict{<:Any, <:Any})
```

Given a `key` and a `value` which is a dictionary, concatenate the `key` string to every other key of the  dictionary `value`. A dictionary of dictionaries will become only a dictionary of values.

Thus, we are "flattening" the inner dictionaries.
