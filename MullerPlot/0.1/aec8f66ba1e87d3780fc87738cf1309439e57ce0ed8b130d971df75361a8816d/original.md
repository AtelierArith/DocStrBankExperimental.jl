```
mullerBounds(n_t_vid, vid_child_Vid)
```

Return lower and upper bounds `xL_t_vid` and `xU_t_vid` of variant bands for creating a Muller plot.

`n_t_vid`: two dimensional Array whose elements are variant clone sizes. The first dimension `_t` is the timepoints at which the measurements occured; the second dimension `_vid` identifies the variant (i.e. the variant id). The first index refers to the wild type. 
`vid_child_Vid`: A nested array indexed by the variant id's. Its elements are 1D Vectors which contain the variant id's of each variant's children.
