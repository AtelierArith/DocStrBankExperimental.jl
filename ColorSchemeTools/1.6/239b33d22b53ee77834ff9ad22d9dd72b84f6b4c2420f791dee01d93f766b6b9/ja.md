```
colorscheme_to_text(cscheme::ColorScheme, schemename, filename;
    category="オランダの画家",   # category
    notes="本当に失われているわけではない" # notes
)
```

Write a ColorScheme to a Julia text file.

## Example

```
colorscheme_to_text(ColorSchemes.vermeer,
    "the_lost_vermeer",          # name
    "/tmp/the_lost_vermeer.jl",  # file
    category="オランダの画家",   # category
    notes="本当に失われているわけではない" # notes
    )
```

and read it back in with:

```
include("/tmp/the_lost_vermeer.jl")
```
