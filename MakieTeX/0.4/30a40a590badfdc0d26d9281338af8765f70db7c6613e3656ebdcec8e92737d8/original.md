```
CachedPDF(pdf::PDFDocument)
```

Holds a PDF document along with a Poppler handle and a Cairo surface to which it has already  been rendered.

## Usage

```julia
CachedPDF(read("path/to/pdf.pdf"), [page = 0])
CachedPDF(read("path/to/pdf.pdf", String), [page = 0])
CachedPDF(PDFDocument(...), [page = 0])
```

## Fields

  * `doc`: A reference to the `PDFDocument` which is cached here.
  * `ptr`: A pointer to the Poppler handle of the PDF.  May be randomly GC'ed by Poppler.
  * `dims`: The dimensions of the PDF page in points, for ease of access.
  * `surf`: A Cairo surface to which Poppler has drawn the PDF.  Permanent and cached.
  * `image_cache`: A cache for a (rendered*image, scale*factor) pair.  This is used to avoid re-rendering the PDF.
