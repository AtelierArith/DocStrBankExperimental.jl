```
interactive_display(fname::String, response_channel::String="", response_channel2::String="", parameter::String="";
    bwd::Bool=false, fig::Any=nothing, backend::Module=Main, kwargs...)::Any
```

Pluto、Jupyter、またはその他のインタラクティブな環境で使用できるインタラクティブなGUIでグリッドを表示します。 `response_channel`は応答チャネルの初期選択を指定し、`response_channel2`は2つ目のラインプロットの応答チャネルの初期選択を指定し、`parameter`はプロットする初期パラメータを指定します。

この関数を使用する前に、[Makie](https://makie.juliaplots.org/)バックエンド（`GLMakie`、`CairoMakie`または`WGLMakie`）をインポートし、図を設定して`fig`キーワード引数を介して渡す必要があります。
