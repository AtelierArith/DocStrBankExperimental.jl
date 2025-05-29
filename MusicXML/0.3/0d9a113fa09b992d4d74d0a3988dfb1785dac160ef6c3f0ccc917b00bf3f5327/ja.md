[`readmusicxml`](@ref)と似ていますが、Julia型に変換せずに使用します。適切な型を使用して変換してください。

# 例

```julia
xml_note = readmusicxml_partial(path_to_file)
Note(xml_note)
```
