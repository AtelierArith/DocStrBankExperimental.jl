```
    pdDocHasPageLabels(doc::PDDoc) -> Bool
```

Returns `true` if the document has page labels defined.

As per PDF Specification 1.7 Section 12.4.2, a document may optionally define page labels (PDF 1.3) to identifyeach page visually on the screen or in print. Page labels and page indices need not coincide: the indices shallbe fixed, running consecutively through the document starting from 0 for the first page, but the labels may be specified in any way that is appropriate for the particular document.

# Example

```
julia> PDFIO.PD.pdDocHasPageLabels(doc)
false
```
