```
@usingany pkg
@usingany pkg1, pkg2, ... 
@usingany pkg: fn
@usingany pkg: fn, @mcr, ... 
@usingany kwarg = true [pkg...]
```

パッケージを利用可能にし、まだであれば `using` キーワードでロードします。

  * 環境の `LOAD_PATH` にパッケージが利用可能であれば、それで問題ありません。
  * 共有環境にパッケージが利用可能であれば、その環境が `LOAD_PATH` に追加されます。
  * それ以外の場合、パッケージがインストール可能であれば、各パッケージをインストールする環境を選択するように促されます。
  * パッケージがどのレジストリにもリストされていない場合、エラーが発生します。

このマクロはキーワード引数で呼び出すことができます：

  * `update_pkg::Bool`: `true` に設定されている場合、マクロによってインポートされるパッケージを最初に更新します。
  * `update_env::Bool`: 現在の `LOAD_PATH` にある共有環境を最初に更新します。
  * `update_all::Bool`: すべての共有環境と現在のプロジェクトを最初に更新します。

Julia バージョンがバージョン管理されたマニフェストをサポートしている場合、更新時に各更新された環境にバージョン管理されたマニフェストが作成されます。詳細は [`make_current_mnf`](@ref) と [`update`](@ref) を参照してください。

`update_all` または `update_env` のキーワード引数が設定されている場合、`@usingany` はインポートするパッケージを指定せずに呼び出すことができます。`update_pkg` のキーワード引数が設定されている場合、インポートするパッケージを指定する必要があります。

このマクロはエクスポートされています。

# 例

```julia-repl
julia> @usingany Foo, Bar
julia> @usingany Baz: quux
julia> @usingany update_all = true
julia> @usingany update_pkg = true Qux
```
