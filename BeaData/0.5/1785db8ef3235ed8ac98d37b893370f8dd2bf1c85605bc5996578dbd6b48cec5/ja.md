```
bea_parametervalues(dataset::String, param_name:: String;
    user_id = USER_ID) -> DataFrame
```

`param_name`の許可された値の`DataFrame`を返し、説明を含みます。

例:

```julia
# ユーザーIDは ~/.beadatarc に保存されています
julia> bea_parametervalues("NIPA", "TableName");

julia> show(ans[1:3, :])
3×2 DataFrame
│ Row │ Value  │ Description                                                                              │
│     │ String │ String                                                                                   │
├─────┼────────┼──────────────────────────────────────────────────────────────────────────────────────────┤
│ 1   │ T10101 │ 表 1.1.1. 前期比の実質国内総生産のパーセント変化 (A) (Q)                             │
│ 2   │ T10102 │ 表 1.1.2. 実質国内総生産のパーセント変化への寄与 (A) (Q)                             │
│ 3   │ T10103 │ 表 1.1.3. 実質国内総生産、数量指数 (A) (Q)                                           │

```
