```
    pdPageGetContents(page::PDPage) -> CosObject
```

Page rendering objects are normally stored in a `CosStream` object in a PDF file. This method provides access to the stream object.

Please refer to the PDF specification for further details.

# Example

```
julia> pdPageGetContents(page)

448 0 obj
<<
	/Length	437
	/FFilter	/FlateDecode
	/F	(/tmp/tmpZnGGFn/tmp5J60vr)
>>
stream
...
endstream
endobj
```
