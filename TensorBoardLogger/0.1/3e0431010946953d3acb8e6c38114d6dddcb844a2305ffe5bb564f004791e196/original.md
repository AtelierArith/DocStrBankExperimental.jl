```
log_custom_scalar(logger, layout::AbstractDict; step = step(logger))
```

Groups multiple scalars in the same plot to be visualized by the CUSTOM*SCALARS plugin. Note that this function sets the metadata: the actual values must be logged separately with `log*value` and referenced with the correct tag.

The `layout` argument is structured as follows:

```
layout = Dict(category => Dict(name => (chart_type, [tag1, tag2, ...])))
```

where `category` is the main tag for the plot, `name` is the plot's name, `chart_type` is one between `tb_multiline` and `tb_margin` and the array of tags contains the actual references to the logged scalars.
