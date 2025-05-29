```
    pdDocGetCosDoc(doc::PDDoc) -> CosDoc
```

PDF document format is developed in two layers. A logical PDF document information is represented over a physical file structure called COS. `CosDoc` is an access object to the physical file structure of the PDF document. To be used for accessing PDF internal objects from document structure when no direct API is available.

One can access any aspect of PDF using the COS level APIs alone. However, they may require you to know the PDF specification in details and it is not the most intuititive.

# Example

```
julia> cosdoc = pdDocGetCosDoc(doc)

CosDoc ==>
	filepath:		/home/sambit/.julia/dev/PDFIO/test/PDFTest-0.0.4/stillhq/3.pdf
	size:			817945
	hasNativeXRefStm:	 false
	Trailer dictionaries: 
	<<
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
	/Size	163
	/Prev	814755
	/Info	146 0 R
	/Root	154 0 R
>>
	<<
	/ID	[<2ff783c9846ab546bd49f709cb7be307> <2ff783c9846ab546bd49f709cb7be307> ]
	/Size	153
>>
```
