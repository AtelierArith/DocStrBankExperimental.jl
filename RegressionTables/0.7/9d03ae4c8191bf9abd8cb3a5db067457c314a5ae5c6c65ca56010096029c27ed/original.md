`R2Within` is the within R-squared of a fixed effects regression. Since the StatsAPI.jl package does not provide a function for this, it is up to each package extension to provide the relevant information. Labels default to:

  * "Within R2" for `AbstractAscii`
  * "Within $R^2$" for `AbstractLatex`
  * "Within <i>R</i><sup>2</sup>" for `AbstractHtml`
