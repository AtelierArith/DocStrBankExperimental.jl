`FStatIVPValue` is the p-value of the first-stage F-statistic of an IV regression. Since the StatsAPI.jl package does not provide a function for this, it is up to each package extension to provide the relevant information. Labels default to:

  * "First-stage p value" for `AbstractAscii`
  * "First-stage $p$ value" for `AbstractLatex`
  * "First-stage <i>p</i> value" for `AbstractHtml`
