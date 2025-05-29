```
set_theme!(theme::Symbol)
```

現在使用するテーマを設定します。デフォルトのDenebテーマ（`:default`）は、以下のグローバル設定を設定します：

```json
{
    "view": {"continuousWidth": 300, "continuousHeight": 300, "step": 25},
    "mark": {"tooltip": true}
}
```

`:default_no_tooltip`テーマは、上記のデフォルトサイズを設定しますが、ツールチップを無効にします。`:empty`テーマは、Vega-Liteのデフォルトの空の設定を使用します。

他に利用可能なテーマは、Vegaのテーマのいずれかです：`:dark`、`:excel`、`:fivethirtyeight`、`:ggplot2`、`:googlecharts`、`:latimes`、`:powerbi`、`:quartz`、`:urbaninstitute`、`:vox`（詳細は https://vega.github.io/vega-themes を参照してください）。この場合、`:default`のグローバル設定が使用されます。

```
set_theme!(config_theme::Symbol, vega_theme::Symbol)
```

グローバル設定テーマ（`:default`、`:default_no_tooltip`、`:empty`）とVegaテーマを設定します（Vegaテーマなしの場合は`vega_theme = :default`を使用します）。

```
set_theme!(config::NamedTuple, [vega_theme::Symbol])
```

ユーザー指定の設定でテーマを設定します。
