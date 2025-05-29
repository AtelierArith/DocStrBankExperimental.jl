```
    CosDoc
```

PDF file structure provides how the objects are arranged in a PDF file. PDF is designed to be accessed in a random access order. Some of the objects in PDF like fonts can be referred from multiple page objects. To address these concerns objects are provided reference identifiers and mappings are provided from various locations in the PDF files. Moreover, to reduce the size of the files, the objects are put inside stream containers and can be compressed. Access to a specific object reference may need several lookups before the actual object can be traced. All these lead to a fairly complex arrangement of objects. `CosDoc` wraps all the object reference schemes and provide a simplified API called [`cosDocGetObject`](@ref) and simplifies object look up.  Thus any PDF object can be classified into the following forms based on how they are represented in a document:

  * *Direct Objects*: Direct objects are defined where they are referred or used.
  * *Indirect Objects*: Indirect objects have reference identifiers, there location in a PDF document is described through a Object Reference identifier.

One can access any aspect of PDF using the COS level APIs alone. However, they may require you to know the PDF specification in details and they are not the most intuititive.
