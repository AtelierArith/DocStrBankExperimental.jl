```
make_colorscheme(indexedlist;
    length=length(indexedlist),
    category="",
    notes="")
```

Make a ColorScheme using an 'indexed list' like this:

```
gist_rainbow = (
       (0.000, (1.00, 0.00, 0.16)),
       (0.030, (1.00, 0.00, 0.00)),
       (0.215, (1.00, 1.00, 0.00)),
       (0.400, (0.00, 1.00, 0.00)),
       (0.586, (0.00, 1.00, 1.00)),
       (0.770, (0.00, 0.00, 1.00)),
       (0.954, (1.00, 0.00, 1.00)),
       (1.000, (1.00, 0.00, 0.75))
)

make_colorscheme(gist_rainbow)
```

The first element of each item is the point on the colorscheme.

Use `length` keyword to set the number of colors in the colorscheme.
