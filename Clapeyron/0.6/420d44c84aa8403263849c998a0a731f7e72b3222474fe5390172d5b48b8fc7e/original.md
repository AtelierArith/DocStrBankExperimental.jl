```
params = getparams(components,locations;kwargs...)
```

returns a `Dict{String,ClapeyronParam}` containing all the parameters found for the list of components in the available CSVs. `locations` are the locations relative to `Clapeyron` database. the available keywords are the ones used ∈ [`ParamOptions`](@ref) if `return_sites` is set to true, `getparams` will add a "sites" value in the params result, containing a `SiteParam` built with the input parameters.

## Single to Pair promotion

When reading multiple CSVs, if a parameter name appears in a single paramter file and in a pair parameter file, the single parameter values will be promoted to be the diagonal values of the pair interaction matrix:

**`my_parameter_single.csv`**

```
Clapeyron Database File
like parameters
species,a
sp1,1000
sp2,700
sp3,850
```

**`my_parameter_pair.csv`**

```
Clapeyron Database File
pair parameters
species1,species2,a
sp1,sp2,875
sp2,sp3,792
sp3,sp1,960

julia> res = getparams(["sp1","sp2"],userlocations = [my_parameter_single.csv,my_parameter_pair.csv])
Dict{String, Clapeyron.ClapeyronParam} with 1 entry:
  "a" => PairParam{Int64}("a")["sp1", "sp2"]

julia> res["a"].values
2×2 Matrix{Int64}:
 1000  875
  875  700
```

This promotion fails only happens in Single-Pair combinations. it fails otherwise.

## In-memory CSV parsing

if you pass any string starting with `Clapeyron Database File`, it will be parsed as a CSV instead of being used as a filepath:

```julia
julia> x = """Clapeyron Database File,
       in memory like parameters
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
"Clapeyron Database File,
in memory parameters [csvtype = like,grouptype = in_memory_read]
species,a,b
sp1,1000,0.05
sp2,700,0.41
"
julia> Clapeyron.getparams(["sp1","sp2"],userlocations = [x])
Dict{String, Clapeyron.ClapeyronParam} with 2 entries:
  "b" => SingleParam{Float64}("b")["sp1", "sp2"]
  "a" => SingleParam{Int64}("a")["sp1", "sp2"]
```

## Special prefixes

There are some special prefixes that are used by the parser to signal some specific behaviour to be done at parsing time, for one CSV or a group of them:

  * `@DB`: replaces the path by the current Clapeyron default database. When doing `getparams(components,["location"])`, the paths are lowered to `getparams(components,userlocations = ["@DB/location"])`.

In a way, is a path shortcut used internally by Clapeyron to parse it's own database. you can change the path where `@DB` points to (or add other path shortcuts), via adding a corresponding entry to the `Clapeyron.SHORT_PATHS` Dict.

  * `@REPLACE`: Any filepath starting with `@REPLACE` will clear all previous appearances of the parameter names found in the CSV that contains the prefix.
  * `@REMOVEDEFAULTS`: it is used alone, and needs to be passed at the first position of the vector of `userlocations`. it will skip parsing of the default parameters:

The effect of the the parser can be summarized by the following examples:

```
model = PCSAFT(["water"],userlocations = ["@REMOVEDEFAULTS"]) #fails, no parameters found, no CSV parsed
model = PCSAFT(["water"],userlocations = ["@REPLACE/empty_params.csv"]) #fails, no parameters found, default parameters parsed and then removed
model = PCSAFT(["water"],userlocations = ["@REPLACE/my_pcsaft_kij.csv"]) #success, default kij parameters replaced by the ones on `my_pcsaft_kij.csv`
model = PCSAFT(["water"],userlocations = ["@REMOVEDEFAULTS","@DB/SAFT/PCSAFT","@DB/properties/molarmass.csv"]) #sucess. default parameters csv removed, and parsed again, using the @DB prefix to point to the default database.
```

You can use the `@REPLACE` keyword in a in-memory CSV by adding it at the start of the string, followed by an space:

```
#This will replace all previous parsed occurences of `a` and `b`
x_replace = """@REPLACE Clapeyron Database File,
in memory like parameters
species,a,b
sp1,1000,0.05
sp2,700,0.41
"""
```

## CSV type detection and group type

The second line of the csv is used for comments and to identify the type of CSV used. for example:

```
x = """Clapeyron Database File
       in memory like parameters
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
```

Will be parsed as a table with single parameter data. if you want more flexibility, you can instead pass the csvtype between brackets:

```
x = """Clapeyron Database File
       i can write anything here, unlike, association [csvtype = like] but the csv type is already specified.
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
```

additionaly, there are some cases when you want to absolutely sure that your types don't clash with the default values. this is the case with different group parametrizations of UNIFAC (Dormund, VTPR, PSRK):

```
julia> model = UNIFAC(["methanol","ethanol"])
UNIFAC{PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}} with 2 components:
 "methanol": "CH3OH" => 1
 "ethanol": "CH2" => 1, "CH3" => 1, "OH (P)" => 1
Group Type: UNIFACDortmund
Contains parameters: A, B, C, R, Q

julia> model = PSRKUNIFAC(["methanol","ethanol"])
UNIFAC{BasicIdeal} with 2 components:
 "methanol": "CH3OH" => 1
 "ethanol": "CH2" => 1, "CH3" => 1, "OH" => 1
Group Type: PSRK
Contains parameters: A, B, C, R, Q
```

The models are the same (`UNIFAC`), but the group parametrizations are different. this is specified with the `grouptype` keyword. for example, if we see `UNIFAC_groups.csv`, it starts with:

```
Clapeyron Database File,
modified UNIFAC (Dortmund) Groups [csvtype = groups,grouptype = UNIFACDortmund]
species,groups
ethane,"[""CH3"" => 2]"
propane,"[""CH3"" => 2, ""CH2"" => 1]"
butane,"[""CH3"" => 2, ""CH2"" => 2]"
...
```

For compatibility reasons, if you pass a CSV without grouptype, it will be accepted, but two CSV with different specified group types cannot be merged:

```
x1 = """Clapeyron Database File
       paramterization 1 [csvtype = like,grouptype = param1]
       species,a,b
       sp1,1000,0.05
       sp2,700,0.41
       """
x2 = """Clapeyron Database File
       fitted to data [csvtype = like,grouptype = fitted]
       species,a,b
       sp1,912,0.067
       sp2,616,0.432
       """
```

If we pass the same parameters, with different group types, the parser will fail

```julia-repl
julia> Clapeyron.getparams(["sp1","sp2"],userlocations = [x1,x2])
ERROR: cannot join two databases with different group types:
current group type: param1
incoming group type: fitted
```

Note, that the parser will not fail if you pass different parameters with different group types (For example if `a` has `param1` group type and `b` has `fit` group type)
