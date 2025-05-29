```
set_ylabels!(
            axs::Array,
            ylabels::Array{String,1};
            fontsize::Number = 16
)
set_ylabels!(
            axs::Array,
            ylabels::String;
            fontsize::Number = 16
)
```

Set Y-axis labels for the axes, given

  * `axs` An array of axis
  * `labels` Y-axis labels
  * `fontsize` Optional: fontsize of the label
