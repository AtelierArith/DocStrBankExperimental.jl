```
append_residue(Backbone::Backbone, torsion_angles::Vector{<:Real}; ideal::BackboneGeometry=DEFAULT_BACKBONE_GEOMETRY)
```

新しいバックボーンを作成するには、`BackboneGeometry`で指定された結合長と結合角を使用して、最初に3つの新しいトーション角（ψ、ω、ϕ）を追加します。

!!! note
    トーション角の順序は、追加する場合と同じです。順序は*逆*ではありません。

