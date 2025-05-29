```julia
velocities(
    frame::Chemfiles.Frame
) -> Chemfiles.ChemfilesArray

```

`Frame`内の速度を配列として取得します。この配列から速度を読み書きできます。フレームのサイズが変更されると（書き込むか、`resize!`を呼び出すことによって）、配列は無効になります。

フレームに速度がない場合、この関数はエラーを返します。この関数を呼び出す前に、`add_velocities!`を使用してフレームに速度を追加できます。
