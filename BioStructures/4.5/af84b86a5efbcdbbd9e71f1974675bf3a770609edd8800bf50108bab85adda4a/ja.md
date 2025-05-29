```
showcontactmap(contact_map)
showcontactmap(io, contact_map)
```

`ContactMap`の表現を`stdout`または指定された`IO`インスタンスに出力します。

完全にプロットされたバージョンは`plot(contact_map)`で取得できますが、それにはPlots.jlが必要です。`showcontactmap`はその依存関係なしで動作します。
