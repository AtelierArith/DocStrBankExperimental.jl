```
CurvilinearGrid2D(x::AbstractArray{T,2}, y::AbstractArray{T,2}, nhalo::Int, discretization_scheme=:MEG6; backend=CPU()) where {T}
```

`x` と `y` 座標を持つ 2D グリッドを作成します。入力座標には、これらの領域で幾何学が未定義であるため、ハロー / ゴーストデータは含まれていません。`nhalo` 引数は、各次元に沿ったハロセルの数を定義します。
