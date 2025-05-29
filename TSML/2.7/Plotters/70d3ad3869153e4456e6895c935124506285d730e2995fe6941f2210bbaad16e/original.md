Plotter(   Dict(     :interactive => false,     :pdfoutput => true   ) )

Plots a TS by default but performs interactive plotting if specified during instance creation.

  * `:interactive` => boolean to indicate whether to use interactive plotting with `false` as default
  * `:pdfoutput` => boolean to indicate whether ouput will be saved as pdf with `false` as default

Example:

csvfilter = CSVDateValReader(Dict(:filename=>fname,:dateformat=>"dd/mm/yyyy HH:MM")) pltr = Plotter(Dict(:interactive => false))

mpipeline = @pipeline csvfilter |> pltr myplot = fit_transform!(mpipeline)

Implements: `fit!`, `transform!`
