```
function callback!(func::Union{Function, ClientsideFunction, String},
    app::DashApp,
    output::Union{Vector{Output}, Output},
    input::Union{Vector{Input}, Input},
    state::Union{Vector{State}, State} = []
    )
```

関数 `func` を呼び出すことで出力を更新するコールバックを作成します。

# 例

```julia
app = dash() do
    html_div() do
        dcc_input(id="graphTitle", value="Let's Dance!", type = "text"),
        dcc_input(id="graphTitle2", value="Let's Dance!", type = "text"),
        html_div(id="outputID"),
        html_div(id="outputID2")

    end
end
callback!(app, [Output("outputID2", "children"), Output("outputID", "children")],
    Input("graphTitle", "value"),
    State("graphTitle", "type")
    ) do inputValue, stateType
    return (stateType * "..." * inputValue, inputValue)
end
```
