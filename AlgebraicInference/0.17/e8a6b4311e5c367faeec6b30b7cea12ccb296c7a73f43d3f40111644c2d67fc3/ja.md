```
InferenceProblem(
    diagram::RelationDiagram,
    hom_map::AbstractDict,
    ob_map::AbstractDict;
    hom_attr::Symbol=:name,
    ob_attr::Symbol=:junction_type,
    var_attr::Symbol=:variable
    check::Bool=true)
```

無向合成を行う推論問題を構築します。
