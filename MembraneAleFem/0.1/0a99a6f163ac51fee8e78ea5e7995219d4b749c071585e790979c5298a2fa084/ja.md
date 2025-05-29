```
solve(p::Params; args...)
```

主な関数で、指定された [`Parameters`](@ref man-params) に対して任意の [`Scenario`](@ref) を解決します。

[`prepare_input`](@ref) を呼び出すことで、[`Mesh`](@ref) 構造体 (`mesh`)、初期位置 (`xms`)、および初期制御点 (`cps`) が最初に生成されます。これらの初期データを使用して、[`run_analysis!`](@ref) が呼び出され、膜の未知数と一連の離散時間での位置を解決します—この間、`xms` と `cps` は繰り返し更新されます。各時間ステップで適切なデータが出力に書き込まれ、最終的な `mesh`、`xms` および `cps` が返されます。

他にも [`Scenario`](@ref)、[`Parameters`](@ref man-params)、[`Mesh`](@ref)、[`prepare_input`](@ref)、[`run_analysis!`](@ref) を参照してください。
