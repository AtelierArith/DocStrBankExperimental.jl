```
setinvalid_range!(df, var_ranges...; setvalmissing = true, ...)
```

Set records with values outside specified ranges to false in :valid column. 

If their is no limit towards small or large values, supply `-Inf` or `Inf` as the minimum or maximum respectively. If there were false values in the :value column before, they are kept false. In addition, set values outside ranges to missing.

# Arguments

  * `df`: DataFrame with column :GPP
  * `var_ranges`: Pair `Varname_symbol => (min,max)`: closed valid interval for  respective column

optional

  * setvalmissing: set to false to prevent replacing values in value column outside ranges to missing.

# Value

df with modified :valid and value columns. 

```jldoctest; output = false
using DataFrames
df = DataFrame(NEE = [missing, 2,3], GPP = 10:10:30)
setinvalid_range!(df, :NEE => (-2.0,4.0), :GPP => (8.0,28.0))
df.valid == [false, true, false]
ismissing(df.GPP[3])
# output
true
```
