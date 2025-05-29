```
interval(a, b)
```

`interval(a, b)` は [a, b] が有効な `Interval` であるかどうかを (非エクスポートの) `is_valid_interval` 関数を使用してチェックします。もし有効であれば、`Interval(a, b)` オブジェクトが返されます。そうでない場合は、警告が表示され、空の区間が返されます。
