```
function subset_invalid_year
```

# 引数

# 

# 例

```jldoctest
julia> using PreprocessMD, Dates, DataFrames

julia> X = DataFrame(name=["Kermit", "Big Bird", "Herry", "Mr. Snuffleupagus", "Rosita", "Julia"], first_appearance=Date.(["1955-05-09", "1969-11-10", "1970-11-09", "1971-11-15", "1991-11-26", "2017-04-10"]))
6×2 DataFrame
 Row │ name               first_appearance
     │ String             Dates.Date
─────┼─────────────────────────────────────
   1 │ Kermit             1955-05-09
   2 │ Big Bird           1969-11-10
   3 │ Herry              1970-11-09
   4 │ Mr. Snuffleupagus  1971-11-15
   5 │ Rosita             1991-11-26
   6 │ Julia              2017-04-10

julia> subset_invalid_year(X, :first_appearance, 1969, 2000)
2×2 DataFrame
 Row │ name    first_appearance
     │ String  Dates.Date
─────┼──────────────────────────
   1 │ Kermit  1955-05-09
   2 │ Julia   2017-04-10

```
