```
InlineString
```

A set of custom string types of various fixed sizes. Each inline string is a custom primitive type and can benefit from being stack friendly by avoiding allocations/heap tracking in the GC. When used in an array, the elements are able to be stored inline since each one has a fixed size. Currently support inline strings from 1 byte up to 255 bytes. See more details by looking at individual docs for [`String1`](@ref), [`String3`](@ref), [`String7`](@ref), [`String15`](@ref), [`String31`](@ref), [`String63`](@ref), [`String127`](@ref), or [`String255`](@ref).
