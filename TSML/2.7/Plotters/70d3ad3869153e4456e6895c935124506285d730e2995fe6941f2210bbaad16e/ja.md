Plotter(   Dict(     :interactive => false,     :pdfoutput => true   ) )

デフォルトではTSをプロットしますが、インスタンス作成時に指定された場合はインタラクティブプロットを実行します。

  * `:interactive` => インタラクティブプロットを使用するかどうかを示すブール値、デフォルトは`false`
  * `:pdfoutput` => 出力がpdfとして保存されるかどうかを示すブール値、デフォルトは`false`

例:

csvfilter = CSVDateValReader(Dict(:filename=>fname,:dateformat=>"dd/mm/yyyy HH:MM")) pltr = Plotter(Dict(:interactive => false))

mpipeline = @pipeline csvfilter |> pltr myplot = fit_transform!(mpipeline)

実装: `fit!`, `transform!`
