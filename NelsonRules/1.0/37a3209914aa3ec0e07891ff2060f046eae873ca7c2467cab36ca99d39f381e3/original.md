Nelson rules are a method in process control of determining whether some measured variable is out of control (unpredictable versus consistent). Rules for detecting "out-of-control" or non-random conditions were first postulated by [Walter A. Shewhart](https://en.wikipedia.org/wiki/Walter_A._Shewhart) in the 1920s. The Nelson rules were first published in the October 1984 issue of the Journal of Quality Technology in an [article by Lloyd S Nelson](https://www.tandfonline.com/doi/abs/10.1080/00224065.1984.11978921).

The rules are applied to a control chart on which the magnitude of some variable is plotted against time. The rules are based on the mean value and the standard deviation of the samples.

More information on the Nelson Rules are available at https://en.wikipedia.org/wiki/Nelson_rules

All rule methods in this module accept the same type of argument and return the same type of return value:

### Arguments

`series::Real[]` : A timeseries vector to check for rule violation. Each entry is for a single unit of time.

### Returns

`Zip{Tuple{Integer[],Integer[]}}`: An iterator of indices and sequence length of sequences that violate the particular Nelson Rule.

See the individual method documentation for rule description, examples and nuances.

Methods are named `ruleN` where `N` goes from 1-8.  To make it easier to call multiple rules programmatically, methods may also be called via `rule(::Val{N}, series)` where `N` goes from 1-8.
