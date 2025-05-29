```
License(; name="MIT", path=nothing, destination="LICENSE")
```

ライセンスファイルを作成します。

## キーワード引数

  * `name::AbstractString`: PkgTemplatesによってサポートされているライセンスの名前。利用可能なライセンスは[こちら](https://github.com/JuliaCI/PkgTemplates.jl/tree/master/templates/licenses)で確認できます。
  * `path::Union{AbstractString, Nothing}`: カスタムライセンスファイルへのパス。このキーワードは`name`よりも優先されます。
  * `destination::AbstractString`: リポジトリのルートに対するファイルの宛先。例えば、`"LICENSE.md"`が望ましいかもしれません。
