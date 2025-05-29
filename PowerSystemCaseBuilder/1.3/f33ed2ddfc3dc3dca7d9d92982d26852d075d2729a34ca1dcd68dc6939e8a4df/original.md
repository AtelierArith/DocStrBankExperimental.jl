build*system(     category::Type{<:SystemCategory},     name::String,     print*stat::Bool = false;     kwargs..., )

Accepted Key Words:

  * `force_build::Bool`: `true` runs entire build process, `false` (Default) uses deserializiation if possible
  * `skip_serialization::Bool`: Default is `false`
  * `system_catalog::SystemCatalog`
  * `assign_new_uuids::Bool`: Assign new UUIDs to the system and all components if  deserialization is used. Default is `true`.
