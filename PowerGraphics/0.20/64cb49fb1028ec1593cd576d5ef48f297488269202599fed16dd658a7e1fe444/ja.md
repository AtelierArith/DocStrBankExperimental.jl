```
report(res::IS.Results, out_path::String, design_template::String)
```

この関数は、[`Weave.jl`](https://weavejl.mpastell.com/stable/)を使用して、読み込む`report_design.jmd`（Julia markdown）ファイルに基づいてLaTeXまたはHTMLファイルを生成します。

例のテンプレートは[こちら](https://github.com/NREL-Sienna/PowerGraphics.jl/blob/main/report_templates/generic_report_template.jmd)で入手できます。

# 引数

  * `results::IS.Results`: プロットする結果
  * `out_path::String`: レポートが生成される場所のフォルダパス
  * `design_template::String = "file_path"`: 関数をJulia markdownレポートデザインに指示します。デフォルトです。

# 例

```julia
results = solve_op_problem!(OpModel)
out_path = "/Users/downloads"
report(results, out_path, template)
```

# 受け入れられるキーワード

  * `doctype::String = "md2html"`: HTMLを作成します。デフォルトはPDF（latex経由）です。
  * `backend::Plots.AbstractBackend = Plots.gr()`: `Plots.jl` [backend](@extref Plots backends)を設定します。
