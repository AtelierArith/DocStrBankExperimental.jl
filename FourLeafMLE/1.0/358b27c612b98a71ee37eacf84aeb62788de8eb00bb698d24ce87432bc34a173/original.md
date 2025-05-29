```
make_averaged_classification_plot(sequence_length,
                                  x_values, y_values, scores;
                                  topology=nothing,
                                  marker_size=nothing,
                                  Hadamard_mode=false)
```

# Description

Using data from `generate_averaged_classification_plot_data`, makes a Felsenstein plot with points representing the propotion of samples whose MLE is concordant with the specified topology.

# Output

Saves a plot in the directory `plots/'
