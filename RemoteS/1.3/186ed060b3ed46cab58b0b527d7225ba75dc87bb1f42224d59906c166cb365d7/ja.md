```
reportbands(in; [layers=Int[]])
```

または

```
reportbands(in, layer;)
```

`in` 入力引数のバンドの説明を報告します。これは GMTimage、GMTgrid、または 'cube' ファイルのファイル名（String）である可能性があります。通常、`cutcube` 関数で作成されたものです。この関数の使用条件が満たされない場合、警告またはエラーメッセージ（警告として捕まえるには深すぎる場合）が発行されます。

  * `layers`: このオプションのパラメータが使用されると、ベクター `layers` のバンドの説明が報告されます。
  * `layer`: 一意のバンド番号を持つスカラー。`reportbands(in, layers=[layer])` の代替形式です。

文字列ベクターを返します。
