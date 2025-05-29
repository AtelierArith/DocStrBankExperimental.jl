```
plot_parameter_distribution(fitted_model, param_priors;
    subplot_titles = Dict(),
    show_distributions = true,
    show_intervals = true,
    prior_color = :green,
    posterior_color = :orange,
    prior_interval_offset = 0,
    posterior_interval_offset = 0.01,
    inner_interval = 0.5,
    outer_interval = 0.8,
    plot_width = 900,
    plot_height = 300)
```

Plot the prior and posterior distributions of the parameters of a fitted model.

# Arguments

  * 'subplot_titles': A dictionary of parameter names and their corresponding plot titles.
  * 'show_distributions': Whether to show full distributions.
  * 'show_intervals': Whether to show uncertainty intervals.
  * 'prior_color': Color of the prior distribution.
  * 'posterior_color': Color of the posterior distribution.
  * 'prior*interval*offset': Offset of the prior interval bars.
  * 'posterior*interval*offset': Offset of the posterior interval bars.
  * 'inner_interval': Size of the inner uncertainty interval.
  * 'outer_interval': Size of the outer uncertainty interval.
  * 'plot_width': Width of the plot.
  * 'plot_height': Height of the plot.
