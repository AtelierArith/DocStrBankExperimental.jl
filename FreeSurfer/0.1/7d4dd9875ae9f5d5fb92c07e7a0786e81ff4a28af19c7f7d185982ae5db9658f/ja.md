```
 trk_write(tr::Tract, outfile::String)
```

`.trk` 形式でファイルに `Tract` 構造体を書き込みます

エラーが発生した場合は true を返します（つまり、書き込まれたバイト数が `Tract` 構造体のサイズに基づいて期待されるものではなかった場合）
