```
set_label(r::RemoteConcept{<:AbstractType},
    new_label_name::AbstractString)
```

With this function we are able to set the label for a given Type. This gives us the chance to rename a given type. But be prepared, this is only allowed if the type is not instantiated by inserted data.
