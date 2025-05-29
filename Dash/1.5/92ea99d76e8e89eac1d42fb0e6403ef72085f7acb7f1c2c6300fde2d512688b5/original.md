```
function callback!(func::Union{Function, ClientsideFunction, String},
    app::DashApp,
    deps...
    )
```

Create a callback that updates the output by calling function `func`. "Flat" version of `callback!` function, `deps` must be $Output..., Input...[,State...]$

# Examples

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
