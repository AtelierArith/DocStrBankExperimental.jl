```
MachOLoadCmd(oh::MachOHandle, CT::Type, header)
```

与えられた `MachOHandle` から `MachOLoadCmd` を構築し、タイプ `CT` のオブジェクトを構築します（これは `load_cmd_type(header)` を介して計算できますが、ディスパッチの目的のために明示的に `MachOLoadCmd()` に渡されます）。
