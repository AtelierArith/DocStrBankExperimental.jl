```
    set!(dict::CosDict, name::CosName, obj::CosObject) -> CosDict

    set!(stm::CosStream, name::CosName, obj::CosObject) -> CosStream

```

Sets the value on a dictionary object. Setting a `CosNull` object deletes the object from the dictionary.

In case of `CosStream` objects the data is added to the extent dictionary.

# Example

```
julia> set!(catalog, cn"Version", cn"1.4")

julia> <<
...
/Version /1.4
...
>>
```
