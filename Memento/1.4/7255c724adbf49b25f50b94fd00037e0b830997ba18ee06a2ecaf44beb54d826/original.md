```
DictFormatter([aliases, serializer])
```

Formats the record to Dict that is amenable to serialization formats such as JSON and then runs the serializer function on the produced dictionary.

# Arguments

  * `aliases::Dict{Symbol, Symbol}`: Mapping where the keys represent aliases and values

represent existing record attributes to include in the dictionary (defaults to all attributes).

  * `serializer::Function`: A function that takes a Dictionary and returns a string. Defaults

to `string(dict)`.
