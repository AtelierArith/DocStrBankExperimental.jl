Similar to [`readmusicxml`](@ref) but without converting it to a Julia type. Use the appropriate type to convert it

# Examples

```julia
xml_note = readmusicxml_partial(path_to_file)
Note(xml_note)
```
