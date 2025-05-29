`FStat` is the F-statistic of the regression. Since the StatsAPI.jl package does not provide a function for this, it is up to each package extension to provide the relevant information. Labels default to:

  * "F" for `AbstractAscii`
  * "$F$" for `AbstractLatex`
  * "<i>F</i>" for `AbstractHtml`

!!! note
    the `FStat` label is used in other labels, so changing it will change those labels as well.

