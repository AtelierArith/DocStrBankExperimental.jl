```
    pdDocGetInfo(doc::PDDoc) -> Dict
```

PDFドキュメントが`Document Info`辞書で利用可能なドキュメント情報を提供します。情報には通常、*作成日、修正日、著者、作成者*などが含まれます。ただし、すべての情報が必須ではありません。したがって、必要なすべての情報がドキュメントに存在しない場合があります。ドキュメントにInfo辞書がまったくない場合、このメソッドは`nothing`を返します。

詳細についてはPDF仕様を参照してください。

# 例

```
julia> pdDocGetInfo(doc)
Dict{String,Union{CDDate, String, CosObject}} with 7 entries:
  "Subject"  => "AU-B Australian Documents"
  "Producer" => "HPA image bureau 1998-1999"
  "Author"   => "IP Australia"
  "ModDate"  => D:19990527113911Z
  "Keywords" => "Patents"
  "Creator"  => "HPA image bureau 1998-1999"
  "Title"    => "199479714D"
```
