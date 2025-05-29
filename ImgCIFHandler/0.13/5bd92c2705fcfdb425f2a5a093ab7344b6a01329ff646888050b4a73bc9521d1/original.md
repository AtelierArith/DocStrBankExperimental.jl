```
imgload(c::CifContainer, a::ImageArchive)
```

Return the image referenced by the first encountered `_array_data.binary_id` in CIF block `c`. `a` is an archive created using `create_archive`.
