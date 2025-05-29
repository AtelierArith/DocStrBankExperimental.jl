```
set_xylabels!(
            axs::Array,
            xlabels::Union{Array{String,1},String},
            ylabels::Union{Array{String,1},String};
            fontsize::Number = 16
)
```

Set X-axis and Y-axis labels for the axes, given

  * `axs` An array of axis
  * `xlabels` X-axis labels
  * `ylabels` Y-axis labels
  * `fontsize` Optional: fontsize of the label
