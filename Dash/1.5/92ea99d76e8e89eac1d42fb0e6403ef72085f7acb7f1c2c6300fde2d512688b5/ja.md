```
function callback!(func::Union{Function, ClientsideFunction, String},
    app::DashApp,
    deps...
    )
```

関数 `func` を呼び出すことで出力を更新するコールバックを作成します。`callback!` 関数の「フラット」バージョンでは、`deps` は $Output..., Input...[,State...]$ でなければなりません。

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
callback!(app,
    Output("outputID2", "children"),
    Output("outputID", "children"),
    Input("graphTitle", "value"),
    State("graphTitle", "type")
    ) do  inputValue, stateType
    return (stateType * "..." * inputValue, inputValue)
end
```
