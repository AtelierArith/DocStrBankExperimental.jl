```
get_indexed_list_color(indexedlist, n)
```

Get the color at a point `n` given an indexed list of triples like this:

```
gist_rainbow = (
       (0.000,   (1.00, 0.00, 0.16)),
       (0.030,   (1.00, 0.00, 0.00)),
       (0.215,   (1.00, 1.00, 0.00)),
       (0.400,   (0.00, 1.00, 0.00)),
       (0.586,   (0.00, 1.00, 1.00)),
       (0.770,   (0.00, 0.00, 1.00)),
       (0.954,   (1.00, 0.00, 1.00)),
       (1.000,   (1.00, 0.00, 0.75))
    )
```

To make a ColorScheme from this type of list, use:

```
make_colorscheme(gist_rainbow)
```
