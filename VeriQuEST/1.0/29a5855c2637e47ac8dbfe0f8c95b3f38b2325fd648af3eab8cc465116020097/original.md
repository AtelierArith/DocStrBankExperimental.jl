```
plot_verification_results(::MaliciousServer, ::Verbose, xdata, ydata, label)
```

Generates a bar plot of verification results for a MaliciousServer in a Verbose mode. The function normalizes the y-data, creates a figure and an axis, plots the data, adds a legend, and returns the figure.

# Arguments

  * `::MaliciousServer`: An instance of `MaliciousServer`.
  * `::Verbose`: An instance of `Verbose`.
  * `xdata`: An array of x-data for the plot.
  * `ydata`: An array of y-data for the plot.
  * `label`: A string to be used as the label in the legend.

# Returns

  * A Figure object containing the generated plot.
