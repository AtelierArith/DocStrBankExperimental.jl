```
walkernumber(v)
```

`v`内のウォーカーの数を計算します。シフトの更新に使用されます。この関数をオーバーロードして、個体数制御を変更します。

ほとんどの場合、`walkernumber(v)`は`norm(v, 1)`と同じです。複素係数を持つ`AbstractDVec`の場合、実部と虚部の1ノルムを`ComplexF64`として別々に報告します。[`Norm1ProjectorPPop`](@ref)を参照してください。
