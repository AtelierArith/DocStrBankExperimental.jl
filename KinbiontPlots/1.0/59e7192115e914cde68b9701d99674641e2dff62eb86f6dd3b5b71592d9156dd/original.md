```
plot_fit_of_file(
Kinbiont_results::Any;
path_to_plot="NA", # path where to save Plots
display_plots=true,# display plots in julia or not
save_plots=false, # save the plot or not
x_size=500,
pt_smoothing_derivative = 7,
y_size =750,
guidefontsize=18,
tickfontsize=16,
legendfontsize=10,
)
```

This function plot all the data from .csv file, note that assume that the first colums is the time

# Arguments:

  * `Kinbiont_results`: The data struct of the results of a "fit  one .csv function" of Kinbiont

# Key Arguments:

  * `path_to_annotation::Any = missing`: The path to the .csv of annotation
  * `path_to_plot= "NA"`:String, path to save the plots.
  * `save_plot=false` :Bool, save the plot or not
  * `display_plots=true`:Bool,  Whether or not diplay the plot in julia
  * `average_replicate=false` Bool, perform or not the average of replicates. Works only if an annotation path is provided
  * `x_size=300` : X Size of the plot,
  * `y_size=300` : y Size of the plot,
  * `tickfontsize = 10` : size of the text of ticks in the plots
  * `guidefontsize = 10` : size of the text of guide in the plots
  * `legendfontsize = 10` : size of the text of legend in the plots

# Output:

  * For this function the output are saved or displayed depending on the values of key arguments.
