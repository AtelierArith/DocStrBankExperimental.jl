```
selectelem(fens::FENodeSet, fes::T; kwargs...) where {T<:AbstractFESet}
```

有限要素を選択します。

# 引数

  * `fens` = 有限要素ノードセット
  * `fes` = 有限要素セット
  * `kwargs` = 選択基準を指定するためのキーワード引数

## 選択基準

### facing

特定の方向を「向いている」すべての「境界」要素を選択します。

```
exteriorbfl = selectelem(fens, bdryfes, facing=true, direction=[1.0, 1.0, 0.0]);
```

または

```
exteriorbfl = selectelem(fens, bdryfes, facing=true, direction=dout, dotmin = 0.99);
```

ここで

```
function dout(xyz)
    return xyz/norm(xyz)
end
```

`xyz`は境界要素の重心の位置です。ここで、有限要素は、法線と方向ベクトルのドット積が`dotmin`より大きい場合に、与えられた方向に「向いている」と見なされます。`dotmin`のデフォルト値は0.01です（これは、有限要素の法線と与えられた方向の間がほぼ90度であることに対応します）。

この選択方法は、表面のような要素（すなわち、境界メッシュ）に対してのみ意味があります。

### label

ラベルに基づいて要素を選択します。

```
rl1 = selectelem(fens, fes, label=1)
```

### box, distance

ノードが満たすいくつかの基準に基づいて要素を選択します。関数`selectnode()`を参照してください。

例：点`from`から`R+inflate`より近いすべての要素を選択します。

```
linner = selectelem(fens, bfes, distance = R, from = [0.0 0.0 0.0],
  inflate = tolerance)
```

例：

```
exteriorbfl = selectelem(fens, bdryfes,
   box=[1.0, 1.0, 0.0, pi/2, 0.0, Thickness], inflate=tolerance);
```

### withnodes

指定されたノード番号のリストにノードが含まれている要素を選択します。

例：

```julia
l = selectelem(fens, fes, withnodes = [13, 14])
```

### flood

指定されたノードから始めて、すべてのFEを接続して選択します。頂点（ノード）を通じた接続で十分です。

例：すべてのFEを接続して選択します（ノード13から開始）：

```julia
l = selectelem(fens, fes, flood = true, startnode = 13)
```

### オプションのキーワード引数

すべてのノードが含まれている場合にのみ要素を考慮しますか？

  * `allin` = ブール値：trueの場合、要素のすべてのノードが基準を満たす必要があります。そうでない場合は、1つで十分です。

# 出力

`felist` = 基準を満たすセットからの有限要素のリスト
