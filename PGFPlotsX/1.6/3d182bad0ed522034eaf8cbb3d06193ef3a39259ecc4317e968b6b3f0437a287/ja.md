```
GroupPlot([options], contents...)
```

グループプロットで、`groupplots`ライブラリを使用したPGFPlotsです。

グローバルオプションの後の`contents`は次のように処理されます：

1. [`Options`](@ref)（つまり`@pgf {}`から）は、指定されたオプションで`\nextgroupplot`を出力します。
2. `nothing`は`\nextgroupplot[group/empty plot]`として出力されます。
3. [`Axis`](@ref)、[`SemiLogXAxis`](@ref)、[`SemiLogYAxis`](@ref)、および[`LogLogAxis`](@ref)は、`options...`を指定した`\nextgroupplot`として出力され、その後に内容が続きます。
4. その他の値、例えば`Plot`は[`print_tex`](@ref)を使用して出力されます。
