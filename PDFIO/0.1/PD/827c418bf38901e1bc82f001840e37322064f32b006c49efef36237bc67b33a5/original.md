```
    pdDocGetPageLabel(doc::PDDoc, pageno::Int) -> String
```

Returns the page label if the page has a page label associated to it.

As per PDF Specification 1.7 Section 12.4.2, a document may optionally define page labels (PDF 1.3) to identify each page visually on the screen or in print. Page labels and page indices need not coincide: the indices shallbe fixed, running consecutively through the document starting from 0 for the first page, but the labels may be specified in any way that is appropriate for the particular document.

# Example

```
julia> pdDocGetPageLabel(doc, 3)
"ii"
```
