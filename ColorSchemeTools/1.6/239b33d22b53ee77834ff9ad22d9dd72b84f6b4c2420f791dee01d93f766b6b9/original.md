```
colorscheme_to_text(cscheme::ColorScheme, schemename, filename;
    category="dutch painters",   # category
    notes="it's not really lost" # notes
)
```

Write a ColorScheme to a Julia text file.

## Example

```
colorscheme_to_text(ColorSchemes.vermeer,
    "the_lost_vermeer",          # name
    "/tmp/the_lost_vermeer.jl",  # file
    category="dutch painters",   # category
    notes="it's not really lost" # notes
    )
```

and read it back in with:

```
include("/tmp/the_lost_vermeer.jl")
```
