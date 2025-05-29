```
loadfile(path::String, read_annotations=true)
```

Load a BDF+ or EDF+ type file. Takes a pathname. Will ignore annotations if second argument is set false. Returns a BEDFPlus structure including header and data.
