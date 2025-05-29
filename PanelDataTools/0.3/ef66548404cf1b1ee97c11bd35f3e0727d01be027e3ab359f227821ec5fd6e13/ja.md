```
paneldf!(df,PID::Symbol,TID:Symbol)
```

`:PID` と `:TID` を `df` に添付し、毎回それらを渡す必要がなくなります。

# 例

```jldoctest
df = DataFrame(id = [1,1,2,2],t = [1,2,1,2],x=[0,1,1,0])
paneldf!(df,:id,:t)
lag!(df,:x) # パネル (:id) と時間 (:t) 列を指定する必要はありません
4×4 DataFrame
 Row │ id     t      x      L1x
     │ Int64  Int64  Int64  Int64?
─────┼──────────────────────────────
   1 │     1      1      0  missing
   2 │     1      2      1        0
   3 │     2      1      1  missing
   4 │     2      2      0        1
```
