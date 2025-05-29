```
ParamTable(type::Symbol,table;
location = nothing,
name = nothing,
grouptype = :unknown,
options = ParamOptions())
```

Creates a clapeyron CSV file and returns the location of that file. the type determines the table type:

  * `:single` creates a table with single parameters
  * `:pair` creates a table with pair parameters
  * `:assoc` creates a table with association parameters
  * `:group` creates a table with association parameters

By default, the name is generated randomly, and the table is stored as a temporary scratch space (provided by Scratch.jl). You can clean said scratch space by using `Clapeyron.cleartemp!()`.

## Examples:

```julia-repl
julia> data = (species = ["water"],Mw = [18.03]) #it could be a Dict, a named tuple, or any Tables.jl compatible table
(species = ["water"], Mw = [18.9])
julia> file = ParamTable(:single,data ,name="water_new_mw")
"C:\Users\user\.julia\scratchspaces\7c7805af-46cc-48c9-995b-ed0ed2dc909a\ParamTables\singledata_water_new_mw.csv"
julia> model = PCSAFT(["water","methanol"],userlocations = [file])
PCSAFT{BasicIdeal} with 2 components:
 "water"
 "methanol"
Contains parameters: Mw, segment, sigma,
epsilon, epsilon_assoc, bondvol
julia> model.params.Mw
SingleParam{Float64}("Mw") with 2 components:
 "water" => 18.9
 "methanol" => 32.042
```
