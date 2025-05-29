```
parse_data_file(filename; units = :si)
parse_data_file(filename; units = :field)
data = parse_data_file("MY_MODEL.DATA")
```

Parse a .DATA file given by the path in `filename` (industry standard input file) into a Dict with String keys. Units will be converted to strict SI unless you pass an alternative unit system like `units = :field`. Setting `units = nothing` will skip unit conversion. Note that the simulators in JutulDarcy.jl assumes that the unit system is internally consistent. It is highly recommended to parse to the SI units if you want to perform simulations with JutulDarcy.jl.

The best publicly available documentation on this format is available from the Open Porous Media (OPM) project's webpages: [OPM Flow manual ](https://opm-project.org/?page_id=955).

# Keyword arguments

  * `warn_parsing=true`: Produce a warning when keywords are not supported (or partially supported) by the parser.
  * `warn_feature=true`: Produce a warning when keywords are supported, but have limited or missing support in the numerical solvers in `JutulDarcy.jl`.
  * `units=:si`: Symbol that indicates the unit system to be used in the output. Setting this to `nothing` will return values without conversion, i.e. exactly what is in the input files. `:si` will use strict SI. Other alternatives are `:field` and `:metric`. `:lab` is currently unsupported.
  * `verbose=false`: Produce verbose output about parsing progress. For larger files, a lot of output will be generated. Useful when figuring out where a parser fails or spends a lot of time.

# Note

This function only covers a small portion of the keywords that exist for various simulators. You will get warnings that indicate the level of support for keywords in both the parser and the numerical solvers when known keywords with limited support. Pull requests for new keywords are welcome!

The SUMMARY section is skipped due to the large volume of available keywords that are not essential to define simulation cases.
