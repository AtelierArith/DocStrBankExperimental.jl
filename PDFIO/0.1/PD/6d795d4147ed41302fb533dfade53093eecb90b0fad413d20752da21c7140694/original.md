```
    pdDocGetPage(doc::PDDoc, num::Int) -> PDPage
    pdDocGetPage(doc::PDDoc, ref::CosIndirectObjectRef) -> PDPage
```

Given a document absolute page number or object reference, provides the associated page object.

# Example

```
julia> page = pdDocGetPage(doc, 1)
PDFIO.PD.PDPageImpl(...)
julia> page = pdDocGetPage(doc, CosIndirectObjectRef(155, 0))
PDFIO.PD.PDPageImpl(...)
```
