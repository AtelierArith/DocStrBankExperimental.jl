A description that can be used to uniquely identify a DataSet.

Four fields are used to describe the target DataSet:

  * `collection`, the name or UUID of the collection (optional).
  * `dataset`, the name or UUID of the dataset.
  * `type`, the type that should be loaded from the dataset.
  * `parameters`, any extra parameters of the dataset that should match.

# Constructors

```julia
Identifier(collection::Union{AbstractString, UUID, Nothing},
           dataset::Union{AbstractString, UUID},
           type::Union{QualifiedType, Nothing},
           parameters::SmallDict{String, Any})
```

# Parsing

An Identifier can be represented as a string with the following form, with the optional components enclosed by square brackets:

```
[COLLECTION:]DATASET[::TYPE]
```

Such forms can be parsed to an Identifier by simply calling the `parse` function, i.e. `parse(Identifier, "mycollection:dataset")`.
