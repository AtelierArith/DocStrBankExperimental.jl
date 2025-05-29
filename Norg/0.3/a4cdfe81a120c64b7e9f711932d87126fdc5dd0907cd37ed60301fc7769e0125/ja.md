Norg文字列をASTに簡単に解析できます。これは*例*としてPlutoノートブックで使用でき、`Base.show`にはASTのための"text/html"タイプのMIMEに対するメソッドがあります。

# 例

```julia-repl
julia> norg"* Norg Header 1 Example"
NorgDocument
└─ (K"Heading1", 2, 11)
   └─ (K"ParagraphSegment", 4, 10)
      ├─ Norg
      ├─
      ├─ Header
      ├─
      ├─ 1
      ├─
      └─ Example
```
