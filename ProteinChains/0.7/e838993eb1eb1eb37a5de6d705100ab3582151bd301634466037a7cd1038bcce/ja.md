```
append_residue(Backbone::Backbone, torsion_angles::Vector{<:Real}; ideal::BackboneGeometry=DEFAULT_BACKBONE_GEOMETRY)
```

`BackboneGeometry`で指定された結合長と結合角を使用して、最後に3つの新しいトーション角（ψ、ω、ϕ）を追加することで新しいバックボーンを作成します。
