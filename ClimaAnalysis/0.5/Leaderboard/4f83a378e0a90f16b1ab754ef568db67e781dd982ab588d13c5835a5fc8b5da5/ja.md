```
reorder_categories(rmse_var::RMSEVariable, categories::Vector{String})
```

`rmse_var`のカテゴリを`categories`に合わせて並べ替えます。

`categories`にあるカテゴリが`rmse_var`のカテゴリに存在しない場合、エラーが発生します。この関数は、`ClimaAnalysis.Visualize.plot_boxplot!`によって生成されるプロットのカテゴリの順序を変更する際に便利です。
