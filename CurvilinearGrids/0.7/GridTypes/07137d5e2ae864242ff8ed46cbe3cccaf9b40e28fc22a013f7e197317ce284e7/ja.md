```
AxisymmetricGrid2D(x::AbstractMatrix{T}, y::AbstractMatrix{T},  nhalo::Int,  snap_to_axis::Bool,  rotational_axis::Symbol;  T=Float64, backend=CPU())
```

`x` と `y` 座標を持つ軸対称の 2D グリッドを作成します。対称軸は `rotational_axis = :x` または `rotational_axis = :y` です。座標が軸上に留まるように `snap_to_axis=True` を設定します。入力座標には、これらの領域で幾何学が未定義であるため、ハロー / ゴーストデータは含まれていません。`nhalo` 引数は、各次元に沿ったハローセルの数を定義します。
