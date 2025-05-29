```
indices(R, iblock)
```

ブロック `iblock` に関連付けられた線形インデックスを `Jets` ブロック空間 `R::JetBSpace` から返します。

# 例

2つの行ブロックと3つの列ブロックを持つブロック演算子を考えます。 `indices` を使用して、その定義域の最初のブロックに関連付けられたベクトルの要素を特定できます：

```
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for irow=1:2, icol=1:3]
indices(domain(A), 1) # インデックス 1:10 を返します
```
