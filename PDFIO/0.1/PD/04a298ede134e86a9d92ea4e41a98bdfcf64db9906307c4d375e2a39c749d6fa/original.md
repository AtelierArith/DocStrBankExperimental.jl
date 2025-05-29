```
    pdPageExtractText(io::IO, page::PDPage) -> IO
```

Extracts the text from the `page`. This extraction works best for tagged PDF files. For PDFs not tagged, some line and word breaks will not be extracted properly.

# Example

Following code will extract the text from a full PDF file.

```
function getPDFText(src, out)
    doc = pdDocOpen(src)
    docinfo = pdDocGetInfo(doc)
    open(out, "w") do io
		npage = pdDocGetPageCount(doc)
        for i=1:npage
            page = pdDocGetPage(doc, i)
            pdPageExtractText(io, page)
        end
    end
    pdDocClose(doc)
    return docinfo
end
```
