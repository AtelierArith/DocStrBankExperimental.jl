```julia
struct Model{GR, ND, BR, TM, CB}
```

`Model`はノードとブランチで構成されています。ノードはブランチを通じて互いに接続されています。`Model`インスタンスはシミュレーションの準備が整っています。

参照: [`Node`](@ref), [`Branch`](@ref)

# フィールド

!!! warning `Model`はシミュレーション可能なユニットです。データがブランチを通じて流れるとき、すなわちコンポーネントの入力出力バスを通じて流れるとき、コンポーネント同士が接続されていることが重要です。参照: [`simulate!`](@ref)
