```
@withcolor ex
```

`ex`が評価される際に`Base.have_color`が`true`に設定されていることを確認してください。`Base.have_color`の元の値はその後に復元されます。

このマクロは特にCIに便利で、デフォルトで`--color=yes`引数なしで`julia`が実行されることは珍しくありません。

```julia
@withcolor print_with_color(:green, "foo")
```
