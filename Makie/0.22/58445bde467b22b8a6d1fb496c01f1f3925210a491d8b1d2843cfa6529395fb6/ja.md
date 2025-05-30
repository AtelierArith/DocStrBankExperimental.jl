```
update_theme!(with_theme::Theme; kwargs...)
```

現在のテーマを段階的に更新します。これは、`with_theme`で指定されたキーまたはキーワード引数を通じて変更されたものだけが変更され、残りはそのまま保持されることを意味します。ネストされた属性も段階的に更新されるか、新しいテーマに属性がない場合は置き換えられます。

# 例

デフォルトのカラーマップを `:greys` に変更するには、以下のようにその属性をキーワード引数として `update_theme!` に渡すことができます。

```julia
update_theme!(colormap=:greys)
```

これは、最初の引数として `Attributes` または `Theme` のオブジェクトを渡すことでも達成できます。

```julia
update_theme!(Attributes(colormap=:greys))
update_theme!(Theme(colormap=:greys))
```
