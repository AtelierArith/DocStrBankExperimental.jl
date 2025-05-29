```
dictvector(vec, [:first, "second", ...]) = DimVector(vec, Dict(1 => :first, 2 => "second", ...))
dictvector(vec, [:first, ...], :axis, :content)
```

Convenient way to define a (short) `DimVector` whose index function is a dictionary labelling the entries. A name for the dimension / axis, and a label for its content, can be supplied too.
