```
readfame(db, args...; 
    namecase=lowercase,
    prefix=nothing, glue="_",
    collect=[], 
    wc_options...)
```

Read data from FAME database into Julia. The data is returned in a [`Workspace`](@ref TimeSeriesEcon.Workspace).

`db` is a [`FameDatabase`](@ref) or a `String`. If `db` is a `String`, the database will be opened in `:readonly` mode and closed after loading the data.

If the db string containing a path to a file, the path should be encapsulated in  escaped double quotes whenever the path contains spaces.

If `db` is the only argument, then all objects in the database will be loaded. Arguments and options can be used to restrict which objects will be loaded.

Each positional argument after the first one should be a string or a Symbol. 

  * If it is a string that contains a wildcard character (`'?'` or `'^'`, see Fame help about wildcards) then we call [`listdb`](@ref) to obtain a list of objects matching the given wildcard. In this case, we pass the given `wc_options...` to [`listdb`](@ref). You can use them to limit the wildcard search to specific class, type, frequency, etc. See [`listdb`](@ref) for details.
  * Otherwise (Symbol or a string not containing wildcard characters), an object with the given name will be loaded. `wc_options...` are ignored, meaning that the object will be loaded no matter its class, type, frequency, etc.

The following options can be used to modify how the Julia identifiers are constructed from the FAME names.

  * `namecase` - FAME identifiers are case-insensitive and FAME always returns them in upper case. By default we convert the names to lower case. You can pass any function that takes a string and returns a string as the value of the `namecase` option. The default is `lowercase`. For example, this may be a good idea if your database contains names with symbols that are not allowed in Julia identifiers. Currently, we just call `Symbol(namecase(fo.name))`, but you may want to substitute such symbols for something else, e.g. `namecase=(x->lowercase(replace(x, "@"=>"_")))`.
  * `prefix`, if given, will be stripped (together with `glue`) from the beginning of the FAME name. If the name does not begin with the given `prefix` then it will remain unchanged. If you want to load only names starting with the given prefix you must use the appropriate wildcard. Default is `prefix=nothing`, which disables this functionality. Note that `prefix=nothing` and `prefix=""` are not the same.
  * `collect` can be a string/symbol, a vector whose elements are strings/symbols or vectors of strings/symbols, etc. If the name begins with one of the given `collect` values (together with the `glue`), then the object will be loaded in a nested [`Workspace`](@ref). The idea is that nested Workspaces written to the database would be loaded in the same structure by providing the list of names of the nested Workspaces in the `collect` option value. See the examples below.
  * `glue` is used to join the `prefix` or the `collect` strings to the rest of the name. Use the same value as in [`writefame`](@ref) in order for this to work.

## Examples

```
julia> w = Workspace(; a = 1, b=TSeries(2020Q1, randn(10)),
       s = MVTSeries(2020M1, (:q, :p), randn(24,2)),
       c = Workspace(; alpha = 0.1, beta = 0.8, 
       n = Workspace(; s = "Hello World")
       ))
Workspace with 4-variables
  a ⇒ 1
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  s ⇒ 24×2 MVTSeries{Monthly} with range 2020M1:2021M12 and variables (q,p)
  c ⇒ Workspace with 3-variables

julia> writefame("data.db", w); listdb("data.db")
7-element Vector{FameObject}:
 A: scalar,numeric,undefined,0:0,0:0
 B: series,precision,quarterly_december,2020:1,2022:2
 C_ALPHA: scalar,precision,undefined,0:0,0:0
 C_BETA: scalar,precision,undefined,0:0,0:0
 C_N_S: scalar,string,undefined,0:0,0:0
 S_P: series,precision,monthly,2020:1,2021:12
 S_Q: series,precision,monthly,2020:1,2021:12

julia> # read only variables in the list
julia> readfame("data.db", "a", "b")
Workspace with 2-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2

julia> # read everything as it is in the database
julia> readfame("data.db")
Workspace with 7-variables
        a ⇒ 1.0
        b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  c_alpha ⇒ 0.1
   c_beta ⇒ 0.8
    c_n_s ⇒ 11-codeunit String
      s_p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
      s_q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # prefix is stripped where it appears (still loading everything)
julia> readfame("data.db", prefix="c")
Workspace with 7-variables
      a ⇒ 1.0
      b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  alpha ⇒ 0.1
   beta ⇒ 0.8
    n_s ⇒ 11-codeunit String
    s_p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
    s_q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # wildcard search, no prefix (name remains unchanged)
julia> readfame("data.db", "s?")
Workspace with 2-variables
  s_p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
  s_q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # prefix (stripped) with matching wildcard search
julia> readfame("data.db", "s?", prefix="s")  
Workspace with 2-variables
  p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
  q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # collect with matching wildcard
julia> readfame("data.db", "c?", collect="c")   
Workspace with 1-variables
  c ⇒ Workspace with 3-variables

julia> # nested collect - matches the original structure of nested Workspaces
julia> readfame("data.db", collect=["c"=>["n"], "s"])  
Workspace with 4-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  c ⇒ Workspace with 3-variables
  s ⇒ Workspace with 2-variables

julia> readfame(""/home/usr/my data directory/data.db"", "a", "b")   
Workspace with 2-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2

```
