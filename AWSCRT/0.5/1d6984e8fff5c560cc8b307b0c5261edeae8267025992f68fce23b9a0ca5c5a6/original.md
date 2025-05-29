```
ShadowFramework(
    connection::MQTTConnection,
    thing_name::String,
    shadow_name::Union{String,Nothing},
    shadow_document::T;
    shadow_document_property_callbacks::Dict{String,ShadowDocumentPropertyUpdateCallback} = Dict{
        String,
        ShadowDocumentPropertyUpdateCallback,
    }(),
    shadow_document_pre_update_callback::ShadowDocumentPreUpdateCallback = (v) -> nothing,
    shadow_document_post_update_callback::ShadowDocumentPostUpdateCallback = (v) -> nothing,
    id = 1,
) where {T}
```

Creates a `ShadowFramework`.

Arguments:

  * `connection (MQTTConnection)`: The connection.
  * `thing_name (String)`: Name of the Thing in AWS IoT under which the shadow document will exist.
  * `shadow_name (Union{String,Nothing})`: Shadow name for a named shadow document or `nothing` for an unnamed shadow document.
  * `shadow_document (AbstractDict)`: The local shadow document. This must include all keys in the shadow documents published by the broker. This must also include a `version (Int)` key which will store the shadow document version. It is recommended that you persist this to disk. You can write the latest state to disk inside `shadow_document_post_update_callback`. You should also then load it from disk and pass it as this parameter during the start of your application.
  * `shadow_document_property_callbacks (Dict{String,ShadowDocumentPropertyUpdateCallback})`: An optional set of callbacks. A given callback will be fired for each update to the shadow document property matching the given key. Note that the callback is fired only when shadow properties are changed. A shadow property change occurs when the value of the shadow property is changed to a new value which is not equal to the prior value. This is implemented using `!isequal()`. Please ensure a satisfactory definition (satisfactory to your application's needs) of `isequal` for all types used in the shadow document. You will only need to worry about this if you are using custom JSON deserialization.
  * `shadow_document_pre_update_callback (ShadowDocumentPreUpdateCallback)`: An optional callback which will be fired immediately before updating any shadow document properties. This is always fired, even if no shadow properties will be changed.
  * `shadow_document_post_update_callback (ShadowDocumentPostUpdateCallback)`: An optional callback which will be fired immediately after updating any shadow document properties. This is fired only if shadow properties were changed.
  * `shadow_document_property_pre_update_funcs (Dict{String,ShadowDocumentPropertyPreUpdateFunction})`: An optional set of functions which customize the update behavior of certain shadow document properties. See [`ShadowDocumentPropertyPreUpdateFunction`](@ref) for more information.
  * `id (Int)`: A unique ID which disambiguates log messages from multiple shadow frameworks.

See also [`ShadowDocumentPropertyUpdateCallback`](@ref), [`ShadowDocumentPreUpdateCallback`](@ref), [`ShadowDocumentPostUpdateCallback`](@ref), [`MQTTConnection`](@ref).

```
!!! note "Limitations"
    Removing properties by setting their desired value to `null` is not currently supported. AWS IoT will remove
    that `null` property from the desired state, but the property will remain in the reported state.
```
