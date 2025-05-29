```
validate_annotations(annotations)
```

`annotations`という推定される`onda.annotation`テーブルの内容に対して、テーブルレベルおよび行レベルの検証チェックを両方実行します。`annotations`を返します。

この関数は、以下のいずれかのケースでエラーをスローします：

  * `Legolas.validate(Tables.schema(annotations), AnnotationV1SchemaVersion())`がエラーをスローする
  * `AnnotationV1(r)`が`Tables.rows(annotations)`内の任意の`r`に対してエラーをスローする
  * `annotations`に重複した`id`を持つ行が含まれている
