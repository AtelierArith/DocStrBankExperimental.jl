```
q"..."
```

[`Query`](@ref)としてリテラル文字列を解析するための省略形です。これは、[`Query`](@ref)`(raw"...")`と同等であり、つまり、文字列内に`\`をエスケープせずに置くことができます（`"`の前を除いて）。これはリテラルクエリにとって非常に便利です（例：`q"/ cell = ATCG\:B1 : batch"` == `Query(raw"/ cell = ATCG\:B1 : batch")` == `Query("/ cell = ATCG\\:B1 : batch")` == `Axis("cell") |> IsEqual("ATCG:B1") |> Lookup("batch")`）。
