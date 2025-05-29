```
get_model(role::Role, type::DataType)
```

Get a shared model from the pool. If the model does not exist yet, it will be created. Only types with default constructor are allowed!

# Example

```julia
@kwdef struct ExampleModel
    my_field::Int = 0
end
role = ExampleRole()
model::ExampleModel = get_model(role, ExampleModel)
model.my_field = 1
model2::ExampleModel = get_model(role, ExampleModel)
# model == model2, it will also be the same for every role!
```
