```
getopt()
getargs(stypes="ss*"; stopatopt=true, mustexhaust=true)
```

Tiny, maximally local, and validating command line arg parsing.

Use in a while loop (`while length(ARGS)>0`):

  * getopt() pops and returns the next option from ARGS; if no option is found (i.e., string not starting with "–" or "-"), returns `nothing` (the arguments that would possibly follow are "naked").
  * getargs() returns all arguments up to the next option; must find at least 1.
  * getargs0() returns all arguments up to the next option (0 or more).
  * getarg() returns one argument (not as vector).
  * getargs("sfii") returns a vector of 4 arguments, a string, a float and two integers. Fails if more or fewer arguments are encountered, or if types do not match.
  * getargs("si*") return a vector with a string argument and 0+ ints.

if `stopatopt` is `false`, all command line strings are treated as arguments (default distinguishes between options and arguments).

if `mustexhaust` is `false`, you can read n arguments, and leave additional, "naked arguments" for later parsing (default fails if there are valid arguments left, i.e., if the next string is not an option).
