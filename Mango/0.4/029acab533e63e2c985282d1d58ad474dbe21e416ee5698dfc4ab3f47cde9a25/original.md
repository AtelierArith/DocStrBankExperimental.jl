```
parse_id(protocol::Protocol{T}, id_data::Any)::T where {T}
```

Parse different types to the correct type (if required). Should be implemented if the id type is not trivial.
