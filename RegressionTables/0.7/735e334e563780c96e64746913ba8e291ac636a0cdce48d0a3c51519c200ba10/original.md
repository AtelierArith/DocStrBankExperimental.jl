`FStatPValue` is the p-value of the F-statistic of the regression. Since the StatsAPI.jl package does not provide a function for this, it is up to each package extension to provide the relevant information. Labels default to:

  * "F p value" for `AbstractAscii`
  * "$F$ $p$ value" for `AbstractLatex`
  * "<i>F</i> <i>p</i> value" for `AbstractHtml`
