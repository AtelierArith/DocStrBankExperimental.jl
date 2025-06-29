```
SolverLogger.Logger
```

A logger designed to print tabulated data that can be updated at any point.  It supports varying verbosity levels, each including all of the information  from previous levels. 

# Constructor

```
SolverLogger.Logger(io=stdout; opts...)
SolverLogger.Logger(filename; opts...)
```

The constructor can take either an `IO` object or a filename, in which case it will  be opened with write permissions, replacing any existing contents.

The keyword arguments `opts` are one of the following:

  * `curlevel` Current verbosity level of the solver. A non-negative integer.
  * `freq` A non-negative integer specifying how often the header row should be printed.
  * `headerstyle` A `Crayon` specifying the style of the header.
  * `linechar` A `Char` that is used for the deliminating row underneath the header. Set to ` ` to not print a row below the header.
  * `enable` Enabled/disabled state of the logger at construction.

# Typical Usage

The fields to be printed are specified before use via [`setentry`](@ref). Here the user can specify properties of the field such as the width of the column, format  specifications (such as number of decimal places, numeric format, alignment, etc.), column index, and even conditional formatting via a [`ConditionalCrayon`](@ref). Each field is assigned a fixed verbosity level, and is only printed if the current verbosity level of the logger, set via [`setlevel!`](@ref) is greater than or equal  to the level of the field.

Once all the fields for the logger have been specified, typical usage is via the  [`@log`](@ref) macro:

```
@log logger "iter" 1
@log logger "cost" cost * 10  # supports expressions
@log logger "alpha" alpha
@log logger alpha             # shortcut for the previous
```

All calls to `@log` overwrite any previous data. Data is only stored in the logger  if the field is active at the current verbosity.

To print the log, the easiest is via the [`printlog`](@ref) function, which will  automatically print the header rows for you, at the frequency specified by  `logger.opts.freq`. The period can be reset (printing a header at the next call to  `printlog`) via [`resetcount!`](@ref). For more control, the header and rows can  be printed directly via [`printheader`](@ref) and [`printrow`](@ref).

The logger can be completely reset via [`resetlogger!`](@ref).

# Enabling / Disabling

The logger can be enable/disabled via `SolverLogging.enable` and `SolverLogging.disable`. This overwrites the verbosity level.
