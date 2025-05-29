```
make_classification_plot(sequence_length,
                         x_values, y_values,
                         categorical_data;
                         marker_size=nothing,
                         Hadamard_mode=false)
```

# Description

Makes a plot using data obtained from the function `generate_classification_plot_data`.

# Arguments

  * `sequence_length` : the size of the data, in base pairs, to be generated for each parameter                    regime (i.e., for each point on the plot)
  * `x_values`, `y_values`, `categorical_data` : the output of `generate_classification_plot_data`.
  * `marker_size` : Optional parameter. Determines the size of the squares made by the scatter plot.                 Depending on the step size (which is automatically deduced from the vectors                 `x_values` and `y_values`), this may need to be adjusted. Ideally, `marker_size`                 should be large enough that the squares are visible and are almost or exactly                 adjacent, but not so large that they overlap. If no value is supplied by the                 user, a sensible default will be chosen, which is 171 divided by                 `max(number_of_x_values,number_of_y_values)`.
  * `Hadamard_mode` : Optional parameter. Specifes the plotting mode. If true, then `x_values` and                   `y_values` are interpreted as Hadamard edge parameters. If false, then they                   are interpreted to be branch length distances measured in expected number of                   mutations per site. This affects the axes and labels of the plot. In order to                   obtain good-looking plots, the value of this variable should be the same as                   the value used when generating the data (otherwise the boxes won't be evenly                   spaced).

# Output

A plot like thos shown in the abstract. The plot is saved as an .svg file to "plots/hadamard-plot.svg".

# Example

To replicate the figure in the abstract, run

```
    sequence_length=1000
    x_values, y_values, categorical_results = generate_classification_plot_data(sequence_length, .01, .01, .99, .99, 300, 300, Hadamard_mode=true)
    make_classification_plot(sequence_length, x_values, y_values, categorical_results, Hadamard_mode=true);
```

This will save an .svg image of the plot to the working directory.
