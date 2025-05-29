```
pivot_wider(df::AbstractDataFrame; names_from =  names_cols, values_from = values_cols)
```

A function to widen a data frame (i.e. unstack)  but in the framework of dplyr. The reference page for the R function is [https://tidyr.tidyverse.org/reference/pivot_wider.html](https://tidyr.tidyverse.org/reference/pivot_wider.html)

# Examples

```
df = DataFrame(x = repeat(1:3,inner = 2,outer = 2),
       a = repeat(4:6,inner = 2,outer = 2),
       b = repeat(7:9,inner = 2,outer = 2),
       val1 = ["ce_val1_1","cf_val1_1","ce_val1_2","cf_val1_2","ce_val1_3","cf_val1_3","de_val1_1",
               "df_val1_1","de_val1_2","df_val1_2","de_val1_3","df_val1_3"],
       val2 = ["ce_val2_1","cf_val2_1","ce_val2_2","cf_val2_2","ce_val2_3","cf_val2_3","de_val2_1",
               "df_val2_1","de_val2_2","df_val2_2","de_val2_3","df_val2_3"],
       cname1 = repeat(["c", "d"], inner = 6),
       cname2 = repeat(["e", "f"], 6)
       )
```

12×7 DataFrame │ Row │ x     │ a     │ b     │ val1      │ val2      │ cname1 │ cname2 │ │     │ Int64 │ Int64 │ Int64 │ String    │ String    │ String │ String │ ├─────┼───────┼───────┼───────┼───────────┼───────────┼────────┼────────┤ │ 1   │ 1     │ 4     │ 7     │ ce*val1*1 │ ce*val2*1 │ c      │ e      │ │ 2   │ 1     │ 4     │ 7     │ cf*val1*1 │ cf*val2*1 │ c      │ f      │ │ 3   │ 2     │ 5     │ 8     │ ce*val1*2 │ ce*val2*2 │ c      │ e      │ │ 4   │ 2     │ 5     │ 8     │ cf*val1*2 │ cf*val2*2 │ c      │ f      │ │ 5   │ 3     │ 6     │ 9     │ ce*val1*3 │ ce*val2*3 │ c      │ e      │ │ 6   │ 3     │ 6     │ 9     │ cf*val1*3 │ cf*val2*3 │ c      │ f      │ │ 7   │ 1     │ 4     │ 7     │ de*val1*1 │ de*val2*1 │ d      │ e      │ │ 8   │ 1     │ 4     │ 7     │ df*val1*1 │ df*val2*1 │ d      │ f      │ │ 9   │ 2     │ 5     │ 8     │ de*val1*2 │ de*val2*2 │ d      │ e      │ │ 10  │ 2     │ 5     │ 8     │ df*val1*2 │ df*val2*2 │ d      │ f      │ │ 11  │ 3     │ 6     │ 9     │ de*val1*3 │ de*val2*3 │ d      │ e      │ │ 12  │ 3     │ 6     │ 9     │ df*val1*3 │ df*val2*3 │ d      │ f      │

```
pivot_wider(df; names_from = [:cname1,:cname2], values_from = [:val1,:val2])
```

3×11 DataFrame │ Row │ x     │ a     │ b     │ val1*c*e  │ val1*c*f  │ val1*d*e  │ val1*d*f  │ val2*c*e  │ val2*c*f  │ val2*d*e  │ val2*d*f  │ │     │ Int64 │ Int64 │ Int64 │ String?   │ String?   │ String?   │ String?   │ String?   │ String?   │ String?   │ String?   │ ├─────┼───────┼───────┼───────┼───────────┼───────────┼───────────┼───────────┼───────────┼───────────┼───────────┼───────────┤ │ 1   │ 1     │ 4     │ 7     │ ce*val1*1 │ cf*val1*1 │ de*val1*1 │ df*val1*1 │ ce*val2*1 │ cf*val2*1 │ de*val2*1 │ df*val2*1 │ │ 2   │ 2     │ 5     │ 8     │ ce*val1*2 │ cf*val1*2 │ de*val1*2 │ df*val1*2 │ ce*val2*2 │ cf*val2*2 │ de*val2*2 │ df*val2*2 │ │ 3   │ 3     │ 6     │ 9     │ ce*val1*3 │ cf*val1*3 │ de*val1*3 │ df*val1*3 │ ce*val2*3 │ cf*val2*3 │ de*val2*3 │ df*val2*3 │
