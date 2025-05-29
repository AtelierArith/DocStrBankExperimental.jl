```julia
show_family_list(
    family_name_or_dir::AbstractString;
    elements
) -> Dict

```

擬似ポテンシャルファミリー内の擬似ポテンシャルをきれいなテーブルでリストします。擬似ポテンシャルが表示される元素は、文字列のリストを渡すことで制限できます。例: ["Ag"]。

```julia
show_family_list(family_name_or_dir; elements)
```

[`packages/PseudoPotentialIO/YkY3g/src/load.jl:95`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/load.jl) で定義されています。
