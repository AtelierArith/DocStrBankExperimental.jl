```
JUA_LocalizedText
```

A mutable struct that defines a localized text comprised of a locale specifier and a text portion. It is the equivalent of a `UA_QualifiedName`, but with memory managed by Julia rather than C.

The following constructor methods are defined:

```
JUA_LocalizedText()
```

creates an empty `JUA_LocalizedText`, equivalent to calling `UA_LocalizedText_new()`.

```
JUA_LocalizedText(locale::Union{AbstractString, JUA_String, Ptr{UA_String}}, text::Union{AbstractString, JUA_String, Ptr{UA_String}})
```

creates a `JUA_LocalizedText` with localization `locale` and text `text`.

```
JUA_LocalizedText(ptr::Ptr{UA_LocalizedText})
```

creates a `JUA_LocalizedText` based on the pointer `ptr`. This is a fallback method that can be used to pass `UA_LocalizedText`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `ptr` needs to be manually cleaned up with `UA_LocalizedText_delete(ptr)` after the object is not needed anymore. It is up to the user to ensure this.
