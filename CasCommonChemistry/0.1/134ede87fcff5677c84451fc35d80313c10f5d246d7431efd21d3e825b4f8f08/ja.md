```
cas(query; api_url = "https://commonchemistry.cas.org/api", fetch=10, skip = 0, pagesize = 100)

クエリ文字列を使用してCAS Common Chemistry APIをクエリします。
一致するレコードのDataFrameを返します。

APIの説明から: https://commonchemistry.cas.org/api-overview
* CAS RN（ダッシュありまたはなし）、SMILES（標準または異性体）、InChI（"InChI="プレフィックスありまたはなし）、InChIKey、および名前での検索を許可します
* 名前での検索では、末尾のワイルドカード（例：car*）を使用できます
* すべての検索は大文字と小文字を区別しません

ワイルドカードクエリは、多くのエントリを返す可能性があり、取得に時間がかかることがあります。したがって、デフォルトでは最初の10件のみが取得されます。総数が報告されます。
fetch = :allを使用して、無条件にすべてを取得します。

query : クエリ文字列。URIエンコードされます
fetch N: 取得する最大レコード数。:allの整数。
skip N : 最初のNレコードをスキップします
pagesize: CAS APIのデフォルトページサイズは100です。より低い値を設定できます。主にデバッグ用です
```
