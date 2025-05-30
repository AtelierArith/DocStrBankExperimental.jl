# キーワード引数:

`title` この要素のヘッダー、デフォルトは "Table of Contents"

`indent` 要素を階層によって垂直に整列させるかどうかのフラグ

`depth` ヘッダー要素を制限する値、範囲は1から6（デフォルト = 3）

`aside` 要素をページの右側に固定する、デフォルトはtrue

# 例:

```julia
TableOfContents()

TableOfContents(title="Experiments 🔬")

TableOfContents(title="📚 Table of Contents", indent=true, depth=4, aside=true)
```
