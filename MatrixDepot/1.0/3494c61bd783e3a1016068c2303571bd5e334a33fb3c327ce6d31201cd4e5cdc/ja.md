julia     MatrixDepot

サンプルおよびテスト行列とそれに付随するデータへのアクセスを提供します。特別なケースを制御する引数を使用して、ローカルで行列のセットが生成されます。別のセットは、公開されている行列コレクションの1つである `SuiteSparse Matrix Collection`（以前の `University of Florida Matrix Collection`）および `Matrix Market Collection` からロードされます。

アクセスは次のようになります。

```
using MatrixDepot

A = matrixdepot("hilb", 10) # ローカルで生成されたヒルベルト行列の次元 (10,10)

A = matrixdepot("HB/1138_bus")     # SuiteSparse Collection の名前付き行列
A = matrixdepot(sp(1))             # 数値IDを使用した同じ行列
A = matrixdepot("Harwell*/*/1138_bus") # Matrix Market Collection からの行列

md = mdopen("*/bfly")   # 追加データを持つ名前付き行列
A = md.A
co = md.coord
tx = md("Gname_10.txt")

md = mdopen("gravity", 10, false) # 右辺と解を持つローカルで生成された例
A = md.A
b = md.b
x = md.x
```

###### コマンド:

```
mdinfo, listdir, listgroups, matrixdepot, mdopen, listdata, mdlist,
metasymbols, setgroup!, deletegroup!.
```

###### セレクタパターン:

```
strings, string-patterns (using "*", "?", "[]", "/", "**"), 正規表現: 名前用
builtin(42), user(3,5), sp(10:11,6,2833), mm(1), mm(:): 整数IDまたはすべてにアクセスするため
sp(pattern), mm(pattern) 他のコレクションの対応する（代替）行列にアクセスするため
```

###### プレディケートパターン:

```
isboolean, isinteger, isreal, iscomplex
isgeneral, issymmetric, ishermitian, isskew
isbuiltin, isuser, islocal, isremote, isloaded, isunloaded
issvdok
keyword(string expression), logical, hasdata(symbol), @pred(expression)

参照: "logical" はすべての種類のパターンの論理的組み合わせのため。
```
