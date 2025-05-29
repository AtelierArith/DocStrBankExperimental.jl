```
    pdDocOpen(filepath::AbstractString) -> PDDoc
```

Opens a PDF document and provides the PDDoc document object for subsequent query into the PDF file. `filepath` is the path to the PDF file in the relative or absolute path format.

Remember to release the document with `pdDocClose`, once the object is no longer required. Although `doc` has certain members, it should normally considered as an opaque handle. 

# Example

```
julia> doc = pdDocOpen("test/PDFTest-0.0.4/stillhq/3.pdf")

PDDoc ==>

CosDoc ==>
	filepath:		/home/sambit/.julia/dev/PDFIO/test/PDFTest-0.0.4/stillhq/3.pdf
	size:			817945
	hasNativeXRefStm:	 false
	Trailer dictionaries: 
	<<
	/Info	146 0 R
	/Prev	814755
	/Size	163
	/Root	154 0 R
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
>>
	<<
	/Size	153
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
>>

Catalog:
154 0 obj
<<
	/Type	/Catalog
	/Pages	152 0 R
>>
endobj

isTagged: none
```
