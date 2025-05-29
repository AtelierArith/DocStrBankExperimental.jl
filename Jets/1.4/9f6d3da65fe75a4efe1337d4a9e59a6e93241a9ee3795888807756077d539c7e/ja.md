```
space(R, iblock)
```

ブロック `iblock` に関連付けられた `Jets` サブスペースを、`Jets` ブロック空間 `R::JetBSpace` から返します。

# 例

2つの行ブロックと3つの列ブロックを持つブロック演算子を考えます。 `space` を使用して、その定義域の最初のブロックに関連付けられたサブスペースを決定できます：

```
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for irow=1:2, icol=1:3]
space(domain(A), 1) # JetSpace(Float64,10)
```
