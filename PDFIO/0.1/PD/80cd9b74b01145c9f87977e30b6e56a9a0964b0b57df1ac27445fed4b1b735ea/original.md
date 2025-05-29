```
    pdDocGetInfo(doc::PDDoc) -> Dict
```

Given a PDF document provides the document information available in the `Document Info` dictionary. The information typically includes *creation date, modification date, author, creator* used etc. However, all information content are not mandatory. Hence, all information needed may not be available in a document. If document does not have Info dictionary at all this method returns `nothing`.

Please refer to the PDF specification for further details.

# Example

```
julia> pdDocGetInfo(doc)
Dict{String,Union{CDDate, String, CosObject}} with 7 entries:
  "Subject"  => "AU-B Australian Documents"
  "Producer" => "HPA image bureau 1998-1999"
  "Author"   => "IP Australia"
  "ModDate"  => D:19990527113911Z
  "Keywords" => "Patents"
  "Creator"  => "HPA image bureau 1998-1999"
  "Title"    => "199479714D"
```
