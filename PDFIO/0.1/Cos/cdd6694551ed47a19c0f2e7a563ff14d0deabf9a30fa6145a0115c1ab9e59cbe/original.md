```
    cosDocGetObject(doc::CosDoc, obj::CosObject) -> CosObject
```

PDF objects are distributed in the file and can be cross referenced from one location to another. This is called as indirect object referencing. However, to extract actual information one needs access to the complete object (direct object). This method provides access to the direct object after searching for the object in the document structure. If an indirect object reference is passed as `obj` parameter the complete `indirect object` (reference as well as all content of the object) are returned. A `direct object` passed to the method is returned as is without any translation. This ensures the user does not have to go through checking the type of the objects before accessing the contents.

# Example

```
julia> cosDocGetObject(doc.cosDoc, CosIndirectObjectRef(555, 0))

555 0 obj
<<
	/Count	18
	/Last	629 0 R
	/First	556 0 R
>>
endobj

julia> cosDocGetObject(doc.cosDoc, cn"DirectObject")
/DirectObject
```
