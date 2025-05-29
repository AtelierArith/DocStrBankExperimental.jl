```
customtype(stack::PluginStack, typename::Symbol, abstract_type::Type, target_module::Module = Main; unique_name = true)
```

Assemble a type with fields provided by the plugins in `stack`.

`abstract_type` will be the supertype of the assembled type.

If `unique_name` == `true`, then `typename` will be suffixed with a structure-dependent id. The  id is generated as a hash of the evaluated expression (with the :TYPE_NAME placeholder used instead of the name), meaning that for the same id will be generated for a given type when the same plugins with the same source code are loaded.

# Examples

Assembling a type `AppStateImpl <: AppState` and parametrizing the app with it. 

```julia
abstract type AppState end

mutable struct CustomFieldsApp{TCustomState}
    state::TCustomState
    function CustomFieldsApp(plugins, hookfns, stateargs...)
        stack = PluginStack(plugins, hookfns)
        state_type = customtype(stack, :AppStateImpl, AppState)
        return new{state_type}(Base.invokelatest(state_type, stateargs...))
    end
end
```

!!! note "The need for `invokelatest`"
    We need to use `invokelatest` to instantiate a newly generated type. To use  the generated type normally, first you have to allow control flow to go to the top-level scope after the type was generated. See also the [docs](https://docs.julialang.org/en/v1/manual/methods/#Redefining-Methods)


!!! warning "Antipattern"
    Assembling state types is an antipattern, because plugins can have their own state. (This may provide better performance in a few cases though) Assembled types can make your code less readable, use them sparingly!

