```
print_model_tree(model; io = stdout)
```

Prints a *tree* of the given model similar to a folder tree printed by the Linux `tree` command.

An example for a feedback-controlled inverted pendulum could look like this

```
julia> print_model_tree(my_model)
└─1 (TypeCT): top-level model / FeedbackSystem
  ├─2 (TypeCT): .inverted_pendulum / NamedTuple
  └─3 (TypeCT): .controller / NamedTuple
```

First, the `model_id` is indicated, following the type (`TypeCT`, `TypeDT` or `TypeHybrid`). Then follows the name of each model in the super model. This is either its field name in the `NamedTuple` passed as `models` or the index in the case of vectors or tuples. Finally, after the slash, the type of each model is indicated. This should either be the name of a `struct` type, or `NamedTuple`.

You can also pass your own IO stream to `print_model_tree` as follows

```julia
print_model_tree(my_buffer, model)
```
