```julia
compile_directory(; ...)
compile_directory(dir; source, archive)

```

`Literate.markdown`を使用して`joinpath(dir, source)`をコンパイルし、ソース、マニフェスト、およびプロジェクトファイルをアーカイブに入れ、フッターとして追加します。

`dir`のデフォルトは`pwd()`です。
