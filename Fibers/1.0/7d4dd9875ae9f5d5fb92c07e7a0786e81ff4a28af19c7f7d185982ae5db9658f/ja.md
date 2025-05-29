```
 trk_write(tr::Tract, outfile::String)
```

`Tract` 構造体を .trk 形式のファイルに書き込みます

エラーが発生した場合（すなわち、書き込まれたバイト数が `Tract` 構造体のサイズに基づいて期待されるものではなかった場合）に true を返します
