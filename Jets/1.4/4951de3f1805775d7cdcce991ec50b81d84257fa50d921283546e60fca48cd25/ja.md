```
@blockop(ex, kwargs)
```

`Jets` ブロックオペレーターを構築します。これは、ブロック行列に類似した Jet オペレーターの組み合わせです。

# 例

1 行ブロックと 3 列ブロックの例：

```julia
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for icol=1:3]
```

2 行ブロックと 3 列ブロックの例。

```
using Pkg
pkg"add Jets JetPack"
using Jets, JetPack
A = @blockop [JopDiagonal(rand(10)) for irow=1:2, icol=1:3]
```
