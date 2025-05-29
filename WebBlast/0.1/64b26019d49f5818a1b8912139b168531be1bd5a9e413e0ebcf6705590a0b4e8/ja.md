```
WebBLAST(query;
    query_names = nothing,
    max_waits = Inf,
    num_hits = 100,
    database = "nt",
    program = "blastn",
    verbosity = 1, 
    option_string = "",
    save_XML_path = nothing,
    blast_URL = "https://blast.ncbi.nlm.nih.gov/Blast.cgi?")
```

```

注意: これは、彼らが「非推奨」としてリストしているAPIを使用して、公共のウェブサービスにクエリを送信することに依存しています。これが長期的に機能することを期待しないでください。また、乱用しないでください。そうすると、より早く停止される可能性があります。

入力する内容:

queryは、文字列または文字列の配列（複数の配列を検索する場合）でなければなりません。これらはヌクレオチドまたはアミノ酸であることが期待されますが、特定のタイプにはこだわりません。データベースとプログラムに一致することを確認してください。

query_namesはnothing（デフォルト）でなければならず、その場合、クエリはquery_1、query_2などとして送信されます。または、クエリの数と同じ数の名前を持つ文字列のベクトルです。

save_XML_pathは、返されたXMLをエクスポートします - おそらくこれが必要になることはありません。

max_waitsは、タイムアウトが発生する前の待機時間（待機ごとに20秒）を制御します。

num_hitsは、返される最大ヒット数を制御します。

databaseとprogramは、変更したい一般的なblastオプションです。例えば、program = "blastp"、database = "pdb"。

option_stringは、BLAST Put呼び出しに挿入したい任意の文字列です。形式は「&MATRIX=PAM230&NUCL_REWARD=2」などでなければなりません。

blast_URLは、アクセスできる場合に別のblastサービスを指すために使用できる文字列です。

返される内容:

[注: これをすべてトラバースする方法を理解するのが面倒な場合は、代わりに```flatten_to_dataframe(WebBLAST(query))```を呼び出してください。]

BLASTから返されたXMLドキュメントを受け取り、EzXMLを通じて処理し、これを辞書の配列に変換します。

基本の配列は、クエリごとに1つの要素を持ちます（1つのクエリの場合、これは長さ1の配列になります）。

各Query辞書には「Query_hit_array」というキーがあり、ヒット辞書の配列を返します。

各ヒットは、複数の「高類似ペア」（または「HSP」）を持つことができるため、ヒット辞書には「Hit_hsps」というキーがあり、これはHSPの配列です。
```
