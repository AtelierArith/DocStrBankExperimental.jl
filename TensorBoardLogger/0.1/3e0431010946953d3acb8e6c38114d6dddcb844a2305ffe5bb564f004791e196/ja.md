```
log_custom_scalar(logger, layout::AbstractDict; step = step(logger))
```

CUSTOM*SCALARSプラグインによって視覚化される同じプロット内の複数のスカラーをグループ化します。この関数はメタデータを設定することに注意してください：実際の値は`log*value`で別々にログされ、正しいタグで参照される必要があります。

`layout`引数は次のように構成されています：

```
layout = Dict(category => Dict(name => (chart_type, [tag1, tag2, ...])))
```

ここで、`category`はプロットのメインタグ、`name`はプロットの名前、`chart_type`は`tb_multiline`と`tb_margin`のいずれかで、タグの配列にはログされたスカラーへの実際の参照が含まれています。
