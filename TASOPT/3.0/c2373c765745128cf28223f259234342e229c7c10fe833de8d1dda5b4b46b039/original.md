```
stickfig(ac::aircraft; plot_obj = nothing, label_fs = 16, 
        annotate_text = true, annotate_length = true, 
        annotate_group = true, show_grid = false)
```

`stickfig` plots a "stick figure" airplane on the plot or subplot object `plot_obj` if provided  (else a new plot is created). This is used in conjuction with other functions like [`plot_details`](@ref) to create summary plots to track progress of optimization or present results.
