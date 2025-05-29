```
readdata(directory::AbstractString, lineparser::Function)::Vector{Problem}
```

指定されたディレクトリ内のすべてのファイルを読み込み、与えられた lineparser を使用して行ごとに `ExampleProblem` に解析します。

*TODO: これを初期化時にすべてのデータをメモリに読み込まないイテレータに変換します。*
