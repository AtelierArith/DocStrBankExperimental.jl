```
get_tables(base, catalog)
```

カタログ内のすべてのテーブルを辞書のリストとして取得します。`Identifier`を使用して実際のデータを取得できます。パラメータが指定されていない場合、データは(CBS)[https://www.cbs.nl] OData3ポータルから取得されます。

オプションのパラメータは次のとおりです：

  * base::String、OData3サーバーのベース名
  * catalog::String、カタログ情報のためのOData3サーバーのパス部分
