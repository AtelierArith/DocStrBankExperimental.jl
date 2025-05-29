```
シーケンス
```

文字列、または文字、文字列、または残基名のベクターのラッパーで、アミノ酸シーケンスに作用する関数をディスパッチします。

# 例

```julia-repl
julia> seq = ["アラニン", "グルタミン酸", "グリシン"];

julia> mass(Sequence(seq))
257.2432

julia> seq = "AEG";

julia> mass(Sequence(seq))
257.2432
```
