```
preview_data(
            xs::Array,
            ys::Array;
            title = randstring(10),
            figsize::Tuple{Number,Number} = (4,3),
            xlab::String = "X label",
            ylab::String = "Y label",
            marker::String = "",
            linestyle::String = "-",
            label_fontsize::Int = 12
)
```

Preview data, given

  * `xs` Array of x
  * `ys` Array of y
  * `title` Axis titile
  * `figsize` Canvas size
  * `xlab` X axis label
  * `ylab` Y axis label
  * `marker` Marker style
  * `linestyle` Line style
  * `label_fontsize` X and Y axes label font size
