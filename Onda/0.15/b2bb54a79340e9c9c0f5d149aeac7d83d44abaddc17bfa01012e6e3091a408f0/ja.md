```
validate_signals(signals)
```

`signals`という推定される`onda.signal`テーブルの内容に対して、テーブルレベルおよび行レベルの検証チェックを実行します。`signals`を返します。

この関数は、以下のいずれかのケースでエラーをスローします：

  * `Legolas.validate(Tables.schema(signals), SignalV2SchemaVersion())`がエラーをスローする
  * `SignalV2(r)`が`Tables.rows(signals)`内の任意の`r`に対してエラーをスローする
  * `signals`が重複した`file_path`を持つ行を含む
