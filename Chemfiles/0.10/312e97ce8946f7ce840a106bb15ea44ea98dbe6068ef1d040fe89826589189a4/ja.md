```julia
positions(
    frame::Chemfiles.Frame
) -> Chemfiles.ChemfilesArray

```

`Frame`内の位置を配列として取得します。位置はこの配列から読み取りおよび書き込みが可能です。フレームのサイズが変更されると（書き込むことによって、または`resize!`を呼び出すことによって）、配列は無効になります。
