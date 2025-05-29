```
BreakpointRef(framecode, stmtidx)
BreakpointRef(framecode, stmtidx, err)
```

特定のステートメントインデックス `stmtidx` における `framecode` のブレークポイントへの参照。エラーによるブレークであれば、それも提供してください。

複雑な制御フローを実行するコマンド（例：`next_line!`）は、対応するステートメントにブレークポイントが設定されていなくても、実行スタックがフレームを切り替えたことを示すために `BreakpointRef` を返すことがあります。
