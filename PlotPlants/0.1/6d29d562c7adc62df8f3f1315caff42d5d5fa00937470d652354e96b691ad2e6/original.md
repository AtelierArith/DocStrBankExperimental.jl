```
set_xlabels!(
            axs::Array,
            xlabels::Array{String,1};
            fontsize::Number = 16
)
set_xlabels!(
            axs::Array,
            xlabels::String;
            fontsize::Number = 16
)
```

Set X-axis labels for the axes, given

  * `axs` An array of axis
  * `labels` X-axis labels
  * `fontsize` Optional: fontsize of the label
