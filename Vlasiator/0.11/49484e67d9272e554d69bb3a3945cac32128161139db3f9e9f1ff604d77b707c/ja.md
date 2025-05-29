```
write_vlsv(filein, fileout, newvars::Vector{Tuple{Vector, String, VarInfo}};
   force=false)
```

`filein`に基づいて新しいVLSV `fileout`を生成し、`newvars`を追加します。`force=true`の場合、既存の`fileout`が上書きされます。
