```
CircularMazeState(corridor::Integer, x::Integer)
```

`CircularMazeState`構造体は、円形迷路内のエージェントの状態を表します。

# フィールド

  * `corridor::Integer`: 廊下の番号。値は1から`n_corridors`までの範囲です。
  * `x::Integer`: 廊下内の状態の位置。値は1から`corridor_length`までの範囲です。
