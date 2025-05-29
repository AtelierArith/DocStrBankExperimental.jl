```
read_city()
read_city(path::AbstractString)
```

デフォルトのチャレンジデータ（[https://storage.googleapis.com/coding-competitions.appspot.com/HC/2014/paris_54000.txt](https://storage.googleapis.com/coding-competitions.appspot.com/HC/2014/paris_54000.txt)）から、または`path`にある同様の形式のテキストファイルから[`City`](@ref)を解析して返します。
