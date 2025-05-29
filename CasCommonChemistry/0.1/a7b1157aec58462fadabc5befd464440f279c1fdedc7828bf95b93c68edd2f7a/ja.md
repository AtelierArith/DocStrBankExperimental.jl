```
cas_search(query; api_url = "https://commonchemistry.cas.org/api", size=10, offset=0)

クエリ文字列を使用してCAS Common Chemistry APIにクエリを送信します。
2つのキーを持つDictを返します：

* "count": 一致するレコードの数
* "results": 最初の`size`結果を説明するDicsのベクター

キーワード引数

size: 返す結果の数。APIはこれを100に制限します
offset: スキップするレコードの数。これは最初の100を超えるレコードを取得するために使用されます
```
