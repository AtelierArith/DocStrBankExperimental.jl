```
shadow_document_post_update_callback(shadow_document::AbstractDict)
```

A callback invoked after the shadow document is updated. The parent [`ShadowFramework`](@ref) will not be locked when this callback is invoked. This is a good place to persist the shadow document to disk.

Arguments:

  * `shadow_document (AbstractDict)`: The updated shadow document.
