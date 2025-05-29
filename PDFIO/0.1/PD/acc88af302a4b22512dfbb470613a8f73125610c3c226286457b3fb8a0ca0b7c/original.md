```
    pdDocGetCatalog(doc::PDDoc) -> CosObject
```

`Catalog` is considered the topmost level object in  PDF document that is subsequently used to traverse and extract information from a PDF document. To be used for accessing PDF internal objects from document structure when no direct API is available.

# Example

```
julia> pdDocGetCatalog(doc)

154 0 obj
<<
	/Pages	152 0 R
	/Type	/Catalog
>>
endobj
```
