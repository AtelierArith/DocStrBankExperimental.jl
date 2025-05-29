```
Note <: PGFPlotsX.TikzElement
```

# Constructors

```julia
Note(;content=missing, anchor=missing ,at=missing, align=missing, captionstyle=missing)
```

# Keyword arguments

  * `content::Union{String, Missing}` is the content of the note.
  * `anchor::Union{Symbol, String, Missing}` specifies the anchor of the note box that is used for alignment. A typical one would be `"north west"`.
  * `at::Any` specifies the location in the axis frame that the anchor should adhere to. A typical one would be `(1, 0)`, which means that the anchor is fixed to the south-east corner of the axis frame.
  * `align::Union{Symbol, String, Missing}` specifies how the note should be aligned. It could be `"left"`, `"right"` or `"center"`.
  * `captionstyle::Union{captionstyle, Missing}` is the caption style of the note.
