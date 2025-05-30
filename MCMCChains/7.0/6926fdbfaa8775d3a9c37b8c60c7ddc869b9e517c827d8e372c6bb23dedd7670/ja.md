```
チェーン
```

パラメータ：

  * `value`: `iter` × `var` × `chains` の軸を持つ `AxisArray` オブジェクト
  * `logevidence` : logevidence を含むフィールド。
  * `name_map` : 各変数をセクションにマッピングする `NamedTuple`。
  * `info` : チェーンに関連する雑多な情報を含む `NamedTuple`。

`info` フィールドは `setinfo(c::Chains, n::NamedTuple)` を使用して設定できます。
