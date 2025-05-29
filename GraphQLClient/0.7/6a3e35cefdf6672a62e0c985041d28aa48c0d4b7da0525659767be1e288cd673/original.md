```
initialise_introspected_struct([client::Client], name::String)
initialise_introspected_struct([client::Client], name::SubString)
initialise_introspected_struct(T::Type)
```

Initialise an introspected struct with all fields set to nothing. If name of type supplied as string, this get the `Type` from `client.introspected_types`.
