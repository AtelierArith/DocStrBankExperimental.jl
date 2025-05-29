```
module Dash
```

[Plotly Dash](https://github.com/plotly/dash) のための Julia バックエンド

# 例

```julia

using Dash
app = dash(external_stylesheets=["https://codepen.io/chriddyp/pen/bWLwgP.css"]) do
    html_div() do
        dcc_input(id="graphTitle", value="Let's Dance!", type = "text"),
        html_div(id="outputID"),
        dcc_graph(id="graph",
            figure = (
                data = [(x = [1,2,3], y = [3,2,8], type="bar")],
                layout = Dict(:title => "Graph")
            )
        )

    end
end
callback!(app, Output("outputID", "children"), Input("graphTitle","value"), State("graphTitle","type")) do value, type
    "You've entered: '$(value)' into a '$(type)' input control"
end
callback!(app, Output("graph", "figure"), Input("graphTitle", "value")) do value
    (
        data = [
            (x = [1,2,3], y = abs.(randn(3)), type="bar"),
            (x = [1,2,3], y = abs.(randn(3)), type="scatter", mode = "lines+markers", line = (width = 4,))
        ],
        layout = (title = value,)
    )
end
run_server(app, HTTP.Sockets.localhost, 8050)
```
