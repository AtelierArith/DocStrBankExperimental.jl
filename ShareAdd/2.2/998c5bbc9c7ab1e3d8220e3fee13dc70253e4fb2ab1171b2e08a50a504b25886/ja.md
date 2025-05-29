```
make_importable(pkg::AbstractString)
make_importable(pkgs::AbstractVector{<:AbstractString})
make_importable(pkg1, pkg2, ...)
make_importable(::Nothing) => :success
```

パッケージをチェックします（名前のみ、UUIDはサポートされていません！）、共有環境にないパッケージのインストールを促し、関連する共有環境を `LOAD_PATH` に追加します。

`make_importable` は内部で `@usingany` に使用されますが、例えば `using` の代わりに `import` ステートメントを使用してパッケージをインポートしたい場合など、別々に使用することもできます。

操作が成功した場合は `:success` を返し、ユーザーがプロンプトのいずれかで「Quit. Do Nothing.」を選択した場合は `nothing` を返します。

利用できないパッケージに対してはエラーをスローします。

# 例

```julia-repl
julia> using ShareAdd
julia> make_importable("Foo")
:success
julia> import Foo 

julia> using ShareAdd
julia> make_importable("Foo")
:success
julia> using Foo: bazaar as baz  # @usingany Foo: bazaar as baz はサポートされていない構文です
```

この関数は公開されていますが、エクスポートされていません。
