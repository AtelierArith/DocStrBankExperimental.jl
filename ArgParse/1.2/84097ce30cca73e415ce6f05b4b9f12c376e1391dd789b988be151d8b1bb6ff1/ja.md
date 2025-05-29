```
@project_version
@project_version(filename::String...)
```

指定されたファイル名のProject.tomlファイルから、コンパイル時にバージョンを読み取ります。ファイル名が指定されていない場合は、`Base.current_project()`がデフォルトとなります。複数の文字列が指定された場合、それらは`joinpath`で結合されます。これは、プロジェクトのバージョンと設定のバージョンを同期させるために、[`ArgParseSettings`](@ref)コンストラクタと一緒に使用することを意図しています。

## 例

```julia
ArgParseSettings(add_version = true, version = @project_version)
```
