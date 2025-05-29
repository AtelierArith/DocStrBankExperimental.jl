```
mutual_information!(
    mi::MutualInformationContainer,
    fixed,
    buffer,
    full_image,
    moving_bbox,
    range_x,
    range_y,
    ::Missing;
    set_buffer!,
    get_buffer_crop,
    prefilter_frame_crop! = x -> nothing,
)
```

Calculates the mutual information of two images at all shifts within the `range_x` and `range_y`. The `fixed` image must already be filtered. This will set the `buffer` and filter its contents using `prefilter_frame_crop!`.
