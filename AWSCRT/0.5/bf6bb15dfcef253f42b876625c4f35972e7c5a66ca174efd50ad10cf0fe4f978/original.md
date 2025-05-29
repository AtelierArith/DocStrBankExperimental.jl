```
shadow_document_property_pre_update_function(shadow_document::AbstractDict, key::String, value)::Bool
```

A function invoked when updating a property in the shadow document. This allows you to replace the update behavior in this package if you want to implement custom update behavior for a given property. The parent [`ShadowFramework`](@ref) will be locked when this function is invoked. The lock is reentrant.

```
!!! warning "Warning"
    This function may only update the given `key`. This function cannot modify other properties in the `shadow_document`.
```

Arguments:

  * `shadow_document (AbstractDict)`: The shadow document being updated.
  * `key (String)`: The key in the `shadow_document` for the value being updated.
  * `value (Any)`: The new value for the `key`.

Returns a `Bool` indicating whether an update was done.
