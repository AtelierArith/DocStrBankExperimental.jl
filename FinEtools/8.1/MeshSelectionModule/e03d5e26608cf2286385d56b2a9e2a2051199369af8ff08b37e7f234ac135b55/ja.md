```
selectnode(fens::FENodeSet; kwargs...)
```

いくつかの基準を使用してノードを選択します。

# 引数

  * `v` = 位置の配列、1行につき1つの位置
  * `kwargs` = キーワード引数/値のペア

## 選択基準

### box

```
nLx = vselect(fens.xyz, box = [0.0 Lx  0.0 0.0 0.0 0.0], inflate = Lx/1.0e5)
```

キーワード 'inflate' は、ボックスの範囲（または距離）を増減させて、境界上にあるノードが除外されるか含まれるかを確実にするために使用できます。

### distance

```
list = selectnode(fens.xyz; distance=1.0+0.1/2^nref, from=[0. 0.],
        inflate=tolerance);
```

指定された点から一定の距離内にあるすべてのノードを見つけます。

### plane

```
candidates = selectnode(fens; plane = [0.0 0.0 1.0 0.0], thickness = h/1000)
```

キーワード `plane` は、その法線（最初の2つまたは3つの数値）と原点からの距離（最後の数値）によって平面を定義します。ノードは平面上にあるか、平面からの距離 `thickness` 内に近い場合に選択されます。法線は単位長であると仮定されます。もしそうでない場合は、内部で正規化されます。

### nearestto

```
nh = selectnode(fens; nearestto = [R+Ro/2, 0.0, 0.0] )
```

指定された位置に最も近いノードを見つけます。

### farthestfrom

```
nh = selectnode(fens; farthestfrom = [R+Ro/2, 0.0, 0.0] )
```

指定された位置から最も遠いノードを見つけます。
