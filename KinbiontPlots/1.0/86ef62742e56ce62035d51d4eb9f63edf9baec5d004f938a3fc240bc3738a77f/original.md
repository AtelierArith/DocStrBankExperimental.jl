```
plot_data(
label_exp::String, 
path_to_data::String; 
path_to_annotation::Any = missing,
path_to_plot="NA",
display_plots=true,
save_plots=false,
overlay_plots=true, 
do_blank_subtraction="NO", vg)
avg_replicate=false, 
correct_negative="thr_correction", 
thr_negative=0.01 ,
blank_value = 0.0,
blank_array = [0.0],
text_size = 10,
x_size =
y_size =
)
```

This function plot all the data from .csv file, note that assume that the first colums is the time

# Arguments:

  * `label_exp::String`: The label of the experiment.
  * `path_to_data::String`: The path to the .csv of data

# Key Arguments:

  * `path_to_annotation::Any = missing`: The path to the .csv of annotation
  * `path_to_plot= "NA"`:String, path to save the plots.
  * `save_plot=false` :Bool, save the plot or not
  * `display_plots=true`:Bool,  Whether or not diplay the plot in julia
  * `overlay_plots =true` :Bool, if true it does one plot overlaying  all dataset curves
  * `blank_subtraction="NO"`: String, how perform the blank subtration, options "NO","avg*subtraction" (subtration of average value of blanks) and "time*avg" (subtration of  time average value of blanks).
  * `average_replicate=false` Bool, perform or not the average of replicates. Works only if an annotation path is provided
  * `blank_value = 0.0`: used only if `path_to_annotation = missing`and `blank_subtraction != "NO "`. It is used as average value of the blank
  * `blank_array = [0.0]`:used only if `path_to_annotation = missing`and `blank_subtraction != "NO "`. It is used as array of the blanks values
  * `correct_negative="thr_correction"`  : String, How to treat negative values after blank subtraction. If `"thr_correction"` it put a thr on the minimum value of the data with blank subracted,   if `"blank_correction"` uses blank distribution to impute negative values, if `"remove"` the values are just removed.
  * `x_size=300` : X Size of the plot,
  * `y_size=300` : y Size of the plot,
  * `text_size = 10` : size of the text in the plots

# Output:

  * For this function the output are saved or displayed depending on the values of key arguments.
