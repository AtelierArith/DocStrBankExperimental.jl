```
    pdDocGetPage(doc::PDDoc, num::Int) -> PDPage
    pdDocGetPage(doc::PDDoc, ref::CosIndirectObjectRef) -> PDPage
```

ドキュメントの絶対ページ番号またはオブジェクト参照を指定すると、関連するページオブジェクトを提供します。

# 例

```
julia> page = pdDocGetPage(doc, 1)
PDFIO.PD.PDPageImpl(...)
julia> page = pdDocGetPage(doc, CosIndirectObjectRef(155, 0))
PDFIO.PD.PDPageImpl(...)
```
