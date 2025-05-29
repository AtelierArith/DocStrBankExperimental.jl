```
preferred_origin(event; verbose=false) -> origin
```

`event`のための推奨されるオリジンを返します。これは、イベントに対して複数のオリジンが指定されている場合に定義される可能性があり、`preferred_origin_id`フィールドが設定されている必要があります。この`event`に対してオリジンが1つだけの場合、それが返されます。このイベントに対して指定された`preferred_origin_id`と一致するオリジンがない場合、最初のオリジンが返され、`verbose=true`のときに警告が表示されます。
