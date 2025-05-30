```
position!(LA::CircularLayout, L::Dict{K,NodePosition}, N::T) where {T <: AbstractEcologicalNetwork} where {K}
```

ノードは円に沿って等間隔で配置され、密接に接続されたノードは互いに近くなります。これはモジュラーネットワークを表現する効率的な方法です。

#### 参考文献

McGuffin, M.J., 2012. Simple algorithms for network visualization: A tutorial. Tsinghua Science and Technology 17, 383–398. https://doi.org/10.1109/TST.2012.6297585
