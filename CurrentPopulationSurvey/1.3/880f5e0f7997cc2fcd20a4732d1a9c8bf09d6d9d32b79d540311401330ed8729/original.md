```
cpsdata(year::Int, month::Int[, vars::Vector{String}])
```

Download/parse CPS microdata files for a given year & month, optionally retaining only the variables specified. There are hundreds of variables so specifying only those that you need will significantly increase efficiency when working with the data. Returns a table which can be easily converted into any data type supported by the Tables.jl interface.

# Arguments

  * `year::Int`: the year for which you want to obtain CPS data.
  * `year::Int`: the month for which you want to obtain CPS data.
  * `vars::Vector{String}`: an optional argument specifying the variables in the microdata file that you

would like to keep.

# Examples

```
data1901 = cpsdata(2019, 1, ["HRINTSTA", "PWORWGT"])
```

If you want to work with the data as a DataFrame:

```
using DataFrames

data1901 = DataFrame(cpsdata(2019, 1, ["HRINTSTA", "PWORWGT"]))
```
