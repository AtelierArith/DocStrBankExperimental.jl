```
imgload(c::CIF)
```

Return the image referenced by the first encountered `_array_data.binary_id` in the first block of CIF file `c`. To avoid re-downloading when multiple images are referenced, first create an archive using `create_archive(c)` and pass this as the second argument.
