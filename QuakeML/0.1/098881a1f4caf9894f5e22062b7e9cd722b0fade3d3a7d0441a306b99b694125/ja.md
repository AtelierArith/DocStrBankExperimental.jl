```
preferred_magnitude(event; verbose=false) -> magnitude
```

`event`のための推奨マグニチュードを返します。これは、イベントに対して複数のマグニチュードが与えられている場合に定義され、`preferred_magnitude_id`フィールドが設定されている場合に適用されます。この`event`に対してマグニチュードが1つだけの場合、それが返されます。このイベントに対して、指定された`preferred_magnitude_id`に一致するマグニチュードがない場合、最初のマグニチュードが返され、`verbose`が`true`の場合は警告が表示されます。
