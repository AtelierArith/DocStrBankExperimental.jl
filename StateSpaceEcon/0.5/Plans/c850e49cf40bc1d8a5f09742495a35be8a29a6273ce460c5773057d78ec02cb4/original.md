```
compare_plans(left, right; options)
compare_plans(file, left, right; options)
compare_plans(Base.stdout, left, right; options)
```

Returns an MVTSeries with summary information comparing the two plans. Each cell in the MVTSeries have an interger value corresponding to the following rubric:

  * 0 -> endogenous in both plans.
  * 1 -> exogenous in the left plan only.
  * 2 -> exogenous in the right plan only.
  * 3 -> exogenous in both plans.

The MVTSeries only includes the overlap between the plans; variables, shocks, and periods only included in oe of the plans will not be part of the return MVTSeries.

A detailed comparison can also be printed to a file with the `outfile` or `io` arguments.

### Options

  * `outfile=""` - save the detailed comparison to the target outfile path, if provided.
  * `io=nothing` - output the detailed comparison to a particular iobuffer.
  * `diff=false` - only populate detailed comparison with variables and shocks  which differ between the plans.
  * `alphabetical=false` - set to `true` to sort the variables. By default variables will be listed in the same order as in the left plan.
  * `exog_mark="X"` - a short string (ideally 1 character) to mark exogenous values.
  * `endo_mark="~"` - a short string (ideally 1 character) to mark endogenous values.
  * `missing_mark="."` - a short string (ideally 1 character) to display when a variable is missing from one of the plans.
  * `delim=" "` - delimiter. Use `","`` to make it a CSV file.
  * `pagelines=0` - Set to a positive integer to enable pagination. Number is interpreted as the number of lines to repeat the header line (the one with the ranges).
  * `summary=false` - print summary on plan differences to stdout.
  * `legend=false` - print legend for comparison matrix to stdout.
