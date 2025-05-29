```
preferred_focal_mechanism(event; verbose=false) -> focal_mechanism
```

`event`のための好ましい焦点メカニズムを返します。これは、イベントに対して複数の焦点メカニズムが与えられており、`preferred_focal_mechanism_id`フィールドが設定されている場合に定義される可能性があります。この`event`に対して焦点メカニズムが1つだけの場合、それが返されます。このイベントに関連付けられた焦点メカニズムが、指定された`preferred_focal_mechanism_id`と一致しない場合、最初の焦点メカニズムが返され、`verbose`が`true`の場合は警告が表示されます。
