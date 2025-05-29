```
select_legend(name; encodings=:color, fields=nothing, bind_options=nothing)
```

`name`という名前の`ParamSpec`を作成し、指定された`encoding`または`field`にバインドされた選択可能な凡例を作成するために他の仕様に組み合わせることができます。凡例のインタラクションをトリガーするイベントをカスタマイズするには、Vegaイベントストリームにマッピングされるプロパティで`bind_options`を設定します（例："dblclick"）。凡例のバインディングに関する詳細情報: https://vega.github.io/vega-lite/docs/bind.html#legend-binding
