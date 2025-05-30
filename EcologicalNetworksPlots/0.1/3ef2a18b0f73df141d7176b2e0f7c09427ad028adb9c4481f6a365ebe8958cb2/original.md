```
position!(LA::CircularLayout, L::Dict{K,NodePosition}, N::T) where {T <: AbstractEcologicalNetwork} where {K}
```

Nodes will be positioned at equal distances along a circle, and nodes that are densely connected will be closer to one another. This is an efficient way to represent modular networks.

#### References

McGuffin, M.J., 2012. Simple algorithms for network visualization: A tutorial. Tsinghua Science and Technology 17, 383–398. https://doi.org/10.1109/TST.2012.6297585
