```julia
set_cell!(
    trajectory::Chemfiles.Trajectory,
    cell::Chemfiles.UnitCell
)

```

`trajectory`に関連付けられた`cell`を設定します。このセルはファイルの読み書き時に使用され、ファイル内の任意の単位セルを置き換えます。
