```
tracklog(io::IO=stdout, obj)
```

Print to `io` tracking information of `obj` sorted by time stamp.

See also: [`@track`]

# Example

```
julia> using DataFrames

julia> @track df = DataFrame(col = [4, 1, 3, 2])
4×1 DataFrame
 Row │ col   
     │ Int64 
─────┼───────
   1 │     4
   2 │     1
   3 │     3
   4 │     2

julia> @track sort!(df)
4×1 DataFrame
 Row │ col   
     │ Int64 
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     4

julia> @track transform!(df, :col => ByRow(log))
4×2 DataFrame
 Row │ col    col_log  
     │ Int64  Float64  
─────┼─────────────────
   1 │     1  0.0
   2 │     2  0.693147
   3 │     3  1.09861
   4 │     4  1.38629

julia> @track transform!(df, :col => ByRow(exp))
4×3 DataFrame
 Row │ col    col_log   col_exp  
     │ Int64  Float64   Float64  
─────┼───────────────────────────
   1 │     1  0.0        2.71828
   2 │     2  0.693147   7.38906
   3 │     3  1.09861   20.0855
   4 │     4  1.38629   54.5982

julia> metadata(df)
Dict{String, String} with 4 entries:
  "track_2022-11-13T22:33:21.952" => "transform!(df, :col => ByRow(log))"
  "track_2022-11-13T22:33:13.295" => "df = DataFrame(col = [4, 1, 3, 2])"
  "track_2022-11-13T22:33:15.797" => "sort!(df)"
  "track_2022-11-13T22:33:25.155" => "transform!(df, :col => ByRow(exp))"

julia> tracklog(df)
df = DataFrame(col = [4, 1, 3, 2])
sort!(df)
transform!(df, :col => ByRow(log))
transform!(df, :col => ByRow(exp))
```
