```
    cosDocOpen(filepath::AbstractString) -> CosDoc
```

Provides the access to the physical file and file structure of the PDF document. Returns a `CosDoc` which can be subsequently used for all query into the PDF files. Remember to release the document with `cosDocClose`, once the object is used.
