```
update_theme!(with_theme::Theme; kwargs...)
```

現在のテーマを段階的に更新します。これは、`with_theme`またはキーワード引数で指定されたキーのみが変更され、残りはそのまま保持されることを意味します。ネストされた属性は、段階的に更新されるか、新しいテーマに属性がない場合は置き換えられます。

# 例

デフォルトのカラーマップを `:greys` に変更するには、以下のようにその属性をキーワード引数として `update_theme!` に渡すことができます。

```
update_theme!(colormap=:greys)
```

これは、`Attributes` または `Theme` のオブジェクトを最初の唯一の位置引数として渡すことでも達成できます：

```
update_theme!(Attributes(colormap=:greys))
update_theme!(Theme(colormap=:greys))
```
