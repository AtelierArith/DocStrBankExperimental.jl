```
    pdDocGetNamesDict(doc::PDDoc) -> CosObject
```

Some information in PDF is stored as name and value pairs not essentially a dictionary. They are all aggregated and can be accessed from one `names` dictionary object in the document catalog. This method provides access to such values in a PDF file. Not all PDF document may have a names dictionary. In such cases, a `CosNull` object may be returned.

Please refer to the PDF specification for further details.

# Example

```
julia> pdDocGetNamesDict(doc)

220 0 obj
<<
	/IDS	123 0 R
	/Dests	119 0 R
	/URLS	124 0 R
>>
endobj
```
