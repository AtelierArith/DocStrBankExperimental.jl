```
write_cutfile(fname::AbstractString, cut::Cut, title::AbstractString="write_cutfileによって作成されたカットファイル")

write_cutfile(fname::AbstractString, cuts::AbstractVector{Cut}, title::AbstractString="write_cutfileによって作成されたカットファイル")
```

`Cut`カットデータをTicra互換のカットファイルに書き込みます。
