```
shadow_document_property_update_callback(value)
```

A callback invoked immediately after a property in the shadow document is updated. The parent [`ShadowFramework`](@ref) will be locked when this callback is invoked. The lock is reentrant.

Arguments:

  * `value (Any)`: The new value of the property in the shadow document.
