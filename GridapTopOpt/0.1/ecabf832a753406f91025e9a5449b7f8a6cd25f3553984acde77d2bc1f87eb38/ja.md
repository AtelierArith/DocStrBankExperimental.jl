```
pload(dir::AbstractString, ranks::AbstractArray{<:Integer})
```

ディレクトリ `dir` に格納された JLD2 ファイルのセットから、MPI ランク `ranks` にインデックスされたパーティション化されたオブジェクトをロードします。
