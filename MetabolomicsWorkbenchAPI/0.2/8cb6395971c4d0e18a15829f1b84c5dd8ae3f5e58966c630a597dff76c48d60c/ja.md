```
mw_match(metabolite_name::String) => DataFrame
```

代謝物名またはPubChem/KEGG/HMDB/ChEBI/LIPID MAPS識別子をRefMetに標準化し、refmet名、式、正確な質量、スーパークラス、メインクラス、サブクラスを取得します。

## 詳細:

> 「match」入力項目は、データベース内のカスタマイズされた同義語テーブルに対して検索を実行します。提出された同義語は、指定された入力値から次のタイプの文字を削除することによって「ファジー」な方法で一致します: <space>*+-/(){}[]*";@。さらに、いくつかの一般的なイオン付加接尾辞（例: [M+H]+）が削除されます。出力項目は無視され、次の出力情報が取得されます: refmet*name、式、正確な質量、メインクラス、サブクラス。


[https://www.metabolomicsworkbench.org/tools/MWRestAPIv1.0.pdf](https://www.metabolomicsworkbench.org/tools/MWRestAPIv1.0.pdf)
