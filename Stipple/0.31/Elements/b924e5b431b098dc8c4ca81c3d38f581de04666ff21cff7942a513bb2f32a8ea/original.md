```
@bind(expr, [type])
```

Binds a model parameter to a Vue component, generating a `v-model` property, optionally defining the parameter type. [https://vuejs.org/v2/api/#v-model](https://vuejs.org/v2/api/#v-model)

### Example

```julia
julia> input("", placeholder="Type your name", @bind(:name))
"<input placeholder="Type your name"  v-model='name' />"

julia> input("", placeholder="Type your name", @bind(:name, :identity))
"<input placeholder="Type your name"  v-model.identity='name' />"
```
