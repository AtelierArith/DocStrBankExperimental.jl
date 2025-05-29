```
direct(elm::Element, spec::Spectrum, mat::Material=spec[:Composition])
direct(elm::Element, specfile::String, mat::Material)
direct(elm::Element, specfile::String)
```

Construct a struct to represent a direct-fit reference. Use with `references(...)` to construct a reference set which may be used to fit multiple references to an unknown spectrum using a "direct" linear fit.
