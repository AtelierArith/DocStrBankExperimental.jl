プロットに `restyle!` と `relayout!` の両方を適用します。レイアウト引数は、`layout` キーワード引数に `Layout` のインスタンスを渡すことで指定されます。

`update` Dict（オプション）とすべてのキーワード引数は、restyle に渡されます。

## 例

```jlcon
julia> p = Plot([scatter(y=[1, 2, 3])], Layout(yaxis_title="this is y"));

julia> print(json(p, 2))
{
  "layout": {
    "margin": {
      "l": 50,
      "b": 50,
      "r": 50,
      "t": 60
    },
    "yaxis": {
      "title": "this is y"
    }
  },
  "data": [
    {
      "y": [
        1,
        2,
        3
      ],
      "type": "scatter"
    }
  ]
}

julia> update!(p, Dict(:marker => Dict(:color => "red")), layout=Layout(title="this is a title"), marker_symbol="star");

julia> print(json(p, 2))
{
  "layout": {
    "margin": {
      "l": 50,
      "b": 50,
      "r": 50,
      "t": 60
    },
    "yaxis": {
      "title": "this is y"
    },
    "title": "this is a title"
  },
  "data": [
    {
      "y": [
        1,
        2,
        3
      ],
      "type": "scatter",
      "marker": {
        "color": "red",
        "symbol": "star"
      }
    }
  ]
}
```
