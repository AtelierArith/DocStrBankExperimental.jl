SimulateInput(fit*input::FitInput{T}                 timestamps*forecast::Vector{DateTime}                 exogenous*forecast::Vector{TimeSeries{T}}                 fit*result::FitResult)

SimulateInputは、Simulate Functionsに必要な唯一の情報です。FitResultは、各FitFunction専用に開発される場合もあれば、一般的なバージョンを使用することもできます。理想的には、フィットからシミュレートに流れるすべての重要な情報はハイパーパラメータに含まれているべきです。
