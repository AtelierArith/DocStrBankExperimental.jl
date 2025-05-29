```
mutual_information!(
    mi::MutualInformationContainer,
    fixed,
    buffer,
    ::Any,
    moving_bbox,
    range_x,
    range_y,
    prev_mis::AbstractArray{Float32,2};
    get_buffer_crop,
    kwargs...
)
```

Calculates the mutual information of two images at all shifts within the `range_x` and `range_y`. Warm-starts the evaluation using previous results (`prev_mis`; the return value from a previous call of this function) and using the previously set and filtered contents of the `buffer`.
