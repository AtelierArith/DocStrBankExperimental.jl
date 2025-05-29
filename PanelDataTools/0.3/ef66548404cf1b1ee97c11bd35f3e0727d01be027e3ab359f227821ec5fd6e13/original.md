```
paneldf!(df,PID::Symbol,TID:Symbol)
```

Attaches `:PID` and `:TID` to `df` so that one doesn't have to pass those all the times.

# Examples

```jldoctest
df = DataFrame(id = [1,1,2,2],t = [1,2,1,2],x=[0,1,1,0])
paneldf!(df,:id,:t)
lag!(df,:x) # No need to specify panel (:id) and time (:t) columns
4×4 DataFrame
 Row │ id     t      x      L1x
     │ Int64  Int64  Int64  Int64?
─────┼──────────────────────────────
   1 │     1      1      0  missing
   2 │     1      2      1        0
   3 │     2      1      1  missing
   4 │     2      2      0        1
```
