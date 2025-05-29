```
WilkinsonTicks(
    k_ideal::Int;
    k_min = 2, k_max = 10,
    Q = [(1.0, 1.0), (5.0, 0.9), (2.0, 0.7), (2.5, 0.5), (3.0, 0.2)],
    granularity_weight = 1/4,
    simplicity_weight = 1/6,
    coverage_weight = 1/3,
    niceness_weight = 1/4
)
```

`WilkinsonTicks` is a thin wrapper over `PlotUtils.optimize_ticks`, the docstring of which is reproduced below:

optimize*ticks(xmin, xmax; extend*ticks::Bool = false,                Q = [(1.0,1.0), (5.0, 0.9), (2.0, 0.7), (2.5, 0.5), (3.0, 0.2)],                k*min = 2, k*max = 10, k*ideal = 5,                granularity*weight = 1/4, simplicity*weight = 1/6,                coverage*weight = 1/3, niceness*weight = 1/4,                strict*span = true, span_buffer = nothing)

Find some reasonable values for tick marks.

This is basically Wilkinson's ad-hoc scoring method that tries to balance tight fit around the data, optimal number of ticks, and simple numbers.

## Arguments:

  * `xmax`:

    The maximum value occurring in the data.
  * `xmin`:

    The minimum value occurring in the data.
  * `extend_ticks`:

    Determines whether to extend tick computation. Defaults to false.
  * `strict_span`:

    True if no ticks should be outside [x*min, x*max]. Defaults to true.
  * `Q`:

    A distribution of nice numbers from which labellings are sampled. Stored in the form (number, score).
  * `k_min`:

    The minimum number of ticks.
  * `k_max`:

    The maximum number of ticks.
  * `k_ideal`:

    The ideal number of ticks.
  * `granularity_weight`:

    Encourages returning roughly the number of labels requested.
  * `simplicity_weight`:

    Encourages nicer labeling sequences by preferring step sizes that appear earlier in Q.   Also rewards labelings that include 0 as a way to ground the sequence.
  * `coverage_weight`:

    Encourages labelings that do not extend far beyond the range of the data, penalizing unnecessary whitespace.
  * `niceness_weight`:

    Encourages labellings to produce nice ranges.

## Returns:

`(ticklocations::Vector{Float64}, x_min, x_max)`

## Mathematical details

Wilkinson’s optimization function is defined as the sum of three components. If the user requests m labels and a possible labeling has k labels, then the components are `simplicity`, `coverage` and `granularity`.

These components are defined as follows:

:$

\begin{aligned}   &\text{simplicity} = 1 - \frac{i}{|Q|} + \frac{v}{|Q|}\
  &\text{coverage}   = \frac{x*{max} - x*{min}}{\mathrm{label}*{max} - \mathrm{label}*{min}}\
  &\text{granularity}= 1 - \frac{\left|k - m\right|}{m} \end{aligned} :$

and the variables here are:

  * `q`: element of `Q`.
  * `i`: index of `q` ∈ `Q`.
  * `v`: 1 if label range includes 0, 0 otherwise.
