```
compare_colors(color_a, color_b, field = :l)
```

2つの色を比較します。Luvカラースペースを使用します。`field`はデフォルトで輝度`:l`ですが、`:u`または`:v`にすることもできます。指定されたフィールドの`color_a`が`color_b`より小さい場合はtrueを返します。
