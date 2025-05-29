```
generate_classification_plot_data(sequence_length,
                                  lower_x, lower_y, upper_x, upper_y,
                                  number_of_x_values, number_of_y_values;
                                  Hadamard_mode=false)
```

# Description

For each pair (x,y) with x and y within some user-specified range, do the following:

(1) generate a single datapoint of length `sequence_length` bp from a quartet tree model with   topology 12|34 such that the branch lengths of leaves 1 and 3 are y and all other branch lengths   are x,

(2) infer the maximum likelihood tree estimate(s) for that datapoint,

(3) determine which binary quartet topologies are compatible with the resulting maximum likelihood   estimate (τ=1 is 12|34, τ=2 is 13|23, and τ=3 is 14|23). 

Then save the pair (x,y) together with the inferred compatible topology classification.

# Arguments

  * `sequence_length` : length in bp of the data to be generated for each parameter regime (x,y)
  * `lower_x`, `lower_y`, `upper_x`, `upper_y` : these specify the lower and upper bounds for the values                                        of x and y
  * `number_of_x_values, number_of_y_values` : the number of (evenly space) values to be chosen and                                            sampled from the interval with specified upper and                                            lower bounds. This determines the step size and hence                                            the resolution of the plot; higher values will result                                            in a plot that is less pixelated but will take longer                                            to produce.
  * `Hadamard_mode` : Optional parameter which determines which of 2 modes the function is run in.                   When `Hadamard_mode = false`, x and y are interpreted as being branch lengths                   measured in expected number of mutations per site (i.e., evolutionary                   distance). When `Hadamard_mode = true1, x and y are interpreted as being                   Hadamard edge parameters, (i.e., which are obtained by applying the function d                   -> exp(-2d) to the evolutionary distances).
