```
    PDDestination
```

Used for variety of purposes to locate a rectangular region in a PDF document. Particularly, used in outlines, actions etc.

The structure can denote a location outside of a document as well like in remote GoTo(GoToR) actions. In such cases, it's best be used with filename additionally. Moreover, page references have no meaning in remote file references. Hence, the `pageno` attribute has been set to `Int` unlike the PDF Spec 32000-2008 12.3.2.2.

```
- `pageno::Int` - Page number location
- `layout::CosName` - Various view layouts are possible. Please review the
```

PDF spec for details.      - `values::Vector{Float32}` - [left, bottom, right, top] sequence array. Not     all values are used. The usage depends on the `layout` parameter.     - `zoom::Float32` - Zoom value for the view. Can be `zero` depending on     - `layout` where it's intrinsic; hence, redundant.
