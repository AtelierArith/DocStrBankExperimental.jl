```
mass(s::Sequence)
```

アミノ酸の配列の質量を返します。`Sequence` 構造体タイプが与えられた場合。

# 例

```julia-repl
julia> seq = ["Alanine", "Glutamic acid", "Glycine"];

julia> mass(Sequence(seq))
257.2432

julia> seq = "AEG";

julia> mass(Sequence(seq))
257.2432

julia> seq = ["ALA", "GLU", "GLY"];

julia> mass(Sequence(seq))
257.2432
```
