```
visualize(
    cpm::CellPotts;
    colorby=:type,
    cellcolors=nothing,
    migrationcolors,
    kwargs...)
```

セルラーポッツモデルの視覚化を生成します。

このプロット関数はPlots.jlに基づいているため、可能なキーワードはすべて渡すことができます。

オプションの`colorby`引数は次のように設定できます：      1. `:type`は細胞のタイプによって細胞に色を付けます     2. `:id`は各細胞にユニークな色を付けます     3. `:none`は細胞に色を付けません 

背景（メディウム）色を変更するには、`background`に色を指定します。

カスタムの色のセットを指定することもできます。例：`colormap = [:red,:blue,:green]`

`migrationcolors`は、MigrationPenaltyが存在する場合にカラーマップを受け入れます（現在3D視覚化には適用できません）。
