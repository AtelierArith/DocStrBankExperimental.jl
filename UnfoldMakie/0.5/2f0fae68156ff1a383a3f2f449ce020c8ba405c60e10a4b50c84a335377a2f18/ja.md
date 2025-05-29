```
to_positions(x, y, z; sphere = [0, 0, 0.])
to_positions(pos::AbstractMatrix; sphere = [0, 0, 0.])
```

3D電極位置を2Dレイアウトに投影します。MNEアルゴリズムの再実装です。

入力が`AbstractMatrix`の場合、`size(pos) = (3, nChannels)`であることを前提としています。

ヒント: PyMNEをロードし、UnfoldMakie PyMNE拡張を有効にした後、MNEオブジェクトから直接位置を取得できます。

**戻り値:** `Vector{Point2{Float64}}`. 
