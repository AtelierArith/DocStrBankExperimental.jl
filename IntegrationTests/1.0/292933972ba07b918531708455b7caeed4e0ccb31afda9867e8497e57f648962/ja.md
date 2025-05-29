```
depending_projects(
    package_name::AbstractString, 
    package_filter::Union{<:AbstractString,Regex}
    project_tree::AbstractDict=build_dependency_graph()
)::Vector{String}
```

`package_name`を依存関係として持つパッケージのリストを返します。

# 引数

  * `package_name`: 依存関係の名前
  * `package_filter`: `package_filter`に一致しないすべてのパッケージを無視します。これにはグラフのトップノードパッケージが含まれます。子ノードは常に`package_name`がチェックされますが、`package_filter`に一致しない場合はトラバースされません。
  * `project_tree`: 依存パッケージを検索するプロジェクトツリー。各（サブ）パッケージは`AbstractDict{String, AbstractDict}`である必要があります。

# 戻り値

与えられた依存関係を持つすべてのパッケージの名前を含む`Vector{String}`。
