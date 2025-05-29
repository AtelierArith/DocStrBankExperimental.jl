```
VariableData
```

Immutable struct to store data related to divisions, variables and values, and their mappings from ints to strings, because the solver only works on ints.

# Constructors

  * `VariableData(schedule::Schedule)::VariableData`

Fields:

  * `divvarval_maps::OrderedDict{Symbol,OrderedDict}`: Keys are a symbol `:subject` or `:teacher`.

Values are map of ints (div) to 2-tuple of vecs of ints (var, val).

  * `divvarval_mapstrs::OrderedDict{Symbol,OrderedDict}`: Same as `div_var_val_map` but with strings instead of ints.
  * `alldivs::Vector{Int}`: Vector of all divs as ints.
  * `allvars::Vector{Int}`: Vector of all vars as ints. (no `:subject` `:teacher` bifurcation)
  * `allvals::Vector{Int}`: Vector of all vals as ints. (no `:subject` `:teacher` bifurcation)
  * `divmap::OrderedDict{Int,String}`: Map from div ints to strings.
  * `varmap::OrderedDict{Int,String}`: Map from variable ints to strings.
  * `valmap::OrderedDict{Int,String}`: Map from values ints to strings.
  * `inversedivmap::OrderedDict{String,Int}`: Inverted `divmap`.
  * `inversevarmap::OrderedDict{String,Int}`: Inverted `varmap`.
  * `inversevalmap::OrderedDict{String,Int}`: Inverted `valmap`.
  * `schedule::Schedule`: Schedule type instance.
