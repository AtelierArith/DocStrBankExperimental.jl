```
    pdPageExtractText(io::IO, page::PDPage) -> IO
```

`page`からテキストを抽出します。この抽出は、タグ付きPDFファイルに最適です。タグが付いていないPDFの場合、一部の行や単語の改行が正しく抽出されないことがあります。

# 例

以下のコードは、フルPDFファイルからテキストを抽出します。

```
function getPDFText(src, out)
    doc = pdDocOpen(src)
    docinfo = pdDocGetInfo(doc)
    open(out, "w") do io
		npage = pdDocGetPageCount(doc)
        for i=1:npage
            page = pdDocGetPage(doc, i)
            pdPageExtractText(io, page)
        end
    end
    pdDocClose(doc)
    return docinfo
end
```
