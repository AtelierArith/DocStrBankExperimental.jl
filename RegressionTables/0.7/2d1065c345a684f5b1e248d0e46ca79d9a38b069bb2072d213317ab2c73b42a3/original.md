`FStatIV` is the first-stage F-statistic of an IV regression. Since the StatsAPI.jl package does not provide a function for this, it is up to each package extension to provide the relevant information. Labels default to:

  * "First-stage F statistic" for `AbstractAscii`
  * "First-stage $F$ statistic" for `AbstractLatex`
  * "First-stage <i>F</i> statistic" for `AbstractHtml`
