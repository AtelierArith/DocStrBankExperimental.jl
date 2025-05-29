```
generate_gridpoints(axisminima, stepsizes, n_intervals_eachaxis, 
    grid::GridType = OnGrid())
```

ハイパー長方形ボックス上にグリッドを形成する点のセットを返します。ボックスは次のように広がります。

  * `grid = OnGrid()` の場合は `(axisminima, axisminima .+ (n_intervals_eachaxis .* stepsizes))` で、
  * `grid = OnCell()` の場合は `(axisminima, axisminima .+ ((n_intervals_eachaxis .+ 1) .* stepsizes))` です。

ここで、各座標軸に沿った最小値 (`axisminima`)、各軸に沿ったステップサイズ (`stepsizes`)、および各軸が分割される等間隔の区間の数を示す区間のセット (`n_intervals_per_axis`) があります。

`grid = OnGrid()` の場合、ビンの起点はグリッドポイントとして取られます。`grid = OnCell()` の場合、追加の区間が加えられ、グリッドは各軸の端から半ビン外側にシフトされるため、グリッドポイントはグリッドセルの中心に位置します。
