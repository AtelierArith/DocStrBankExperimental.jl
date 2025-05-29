```
show_parameters(model) -> DataFrame
```

モデル内のすべての反応のパラメータを取得します。

# 例:

VS Codeのテーブルビューアを使用して、すべてのモデルパラメータを表示します:

```
julia> vscodedisplay(PB.show_parameters(run.model))
```

スプレッドシートにインポートするために、すべてのモデルパラメータをcsvとして書き出します:

```
julia> CSV.write("pars.csv", PB.show_parameters(run.model))
```
