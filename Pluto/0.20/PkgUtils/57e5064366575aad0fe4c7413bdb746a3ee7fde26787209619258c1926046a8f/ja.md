```julia
update_notebook_environment(notebook_path::String; backup::Bool=true, level::Pkg.UpgradeLevel=Pkg.UPLEVEL_MAJOR)
```

ノートブックファイルに埋め込まれたパッケージ環境で`Pkg.update`を呼び出し、ノートブックファイルを変更します。`level`キーワード引数には[`Pkg.UpgradeLevel`](@ref)を渡すことができます。バックアップファイルはデフォルトで作成されます。
