```
setparams!(d, params)
```

`d`のパラメータを`params`のキーを使用して設定します。

初期化後に`d.ui.ranges`から利用可能なパラメータをUIRange構造体として抽出できます。

# 例

```julia-repl
julia> d = init!(compile("process = nentry("v", 0, 0, 1, 0.001);"))
julia> d.ui.ranges
Dict{String, Faust.UIRange} with 1 entry:
  "/score/v" => UIRange(0.0, 0.0, 1.0, 0.001)
julia> setparams!(d, Dict("/score/v" => 0.5f0))
```
