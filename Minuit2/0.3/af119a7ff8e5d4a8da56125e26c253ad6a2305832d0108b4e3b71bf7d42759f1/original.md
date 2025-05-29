```
minos!(m::Minuit, name::String)
```

Run Minos algorithm to compute asymmetric errors for a single parameter.

The Minos algorithm uses the profile likelihood method to compute (generally asymmetric) confidence intervals. It scans the negative log-likelihood or (equivalently) the least-squares cost function around the minimum to construct a confidence interval.

## Arguments

  * `m::Minuit` : The Minuit object to minimize.
  * `parameters::AbstractVector{String}` : Names of the parameters to compute the Minos errors for.
  * `cl::Number` : Confidence level of the interval. If not set, a standard 68 %  interval is computed (default). If 0 < cl < 1, the value is interpreted as  the confidence level (a probability). For convenience, values cl >= 1 are  interpreted as the probability content of a central symmetric interval  covering that many standard deviations of a normal distribution. For  example, cl=1 is interpreted as 68.3 %, and cl=2 is 84.3 %, and so on. Using  values other than 0.68, 0.9, 0.95, 0.99, 1, 2, 3, 4, 5 require the scipy module.
  * `ncall::Int` : Limit the number of calls made by Minos. If 0, an adaptive internal  heuristic of the Minuit2 library is used (Default: 0).

## Notes

Asymptotically (large samples), the Minos interval has a coverage probability equal to the given confidence level. The coverage probability is the probability for the interval to contain the true value in repeated identical experiments.

The interval is invariant to transformations and thus not distorted by parameter limits, unless the limits intersect with the confidence interval. As a rule-of-thumb: when the confidence intervals computed with the Hesse and Minos algorithms differ strongly, the Minos intervals are preferred. Otherwise, Hesse intervals are preferred.

Running Minos is computationally expensive when there are many fit parameters. Effectively, it scans over one parameter in small steps and runs a full minimisation for all other parameters of the cost function for each scan point. This requires many more function evaluations than running the Hesse algorithm.
