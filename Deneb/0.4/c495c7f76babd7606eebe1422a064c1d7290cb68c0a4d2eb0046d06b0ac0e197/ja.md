```
resolve(type; channels...)
resolve(type, channel, option)
```

`ResolveSpec`を作成します。`type`は定義される解決を示します：`scale`、`axis`、または`legend`です。

スケールの場合、解決はすべてのチャネルに対して指定できます。軸の場合、解決は位置チャネル（`x`、`y`、`xOffset`、`yOffset`）に対して定義できます。凡例の場合、解決は非位置チャネル（`color`、`opacity`、`shape`、および`size`）に対して定義できます。

スケール、軸、または凡例を解決するための2つのオプションがあります：`shared`と`independent`。独立したスケールは独立した軸と凡例を意味します。

デフォルトはVega-Liteの[documentation](https://vega.github.io/vega-lite/docs/resolve.html)に記載されています。

# 例

```
resolve(:scale, color=:independent)
```
