```
verify(object, provenance::Provenance) -> Bool
```

`provenance` が `object` によって生成されたかどうかを確認します。

必要な暗号化メソッドを提供するパッケージによって拡張される予定です。デフォルトでは、この関数は `Provenance{NoSignature}` データで動作し、常に成功裏に検証されます。
