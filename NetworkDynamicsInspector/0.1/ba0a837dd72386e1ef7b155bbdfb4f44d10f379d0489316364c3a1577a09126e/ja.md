```
inspect(sol; restart=false, reset=false, display=nothing)
```

GUIのメインエントリーポイント。サーバーを起動し、解決策 `sol` のアプリを提供します。

  * `restart`: `true` の場合、表示が再起動されます（つまり、新しいElectronウィンドウ、新しいサーバー、または新しいブラウザタブ）。
  * `reset`: `true` の場合、新しい解決策 `sol` でアプリの状態がリセットされます。
  * `display=CURRENT_DISPLAY[]`: `BrowserDisp()`、`ServerDisp()`、または `ElectronDisp()` である可能性があります。デフォルトでは、現在の表示が使用されます（デフォルトは `BrowserDisp()`）。
