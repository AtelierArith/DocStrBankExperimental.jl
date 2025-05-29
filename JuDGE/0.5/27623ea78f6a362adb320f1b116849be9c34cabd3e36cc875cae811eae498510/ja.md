```
capitalcosts(model, expr)
```

現在のノードでの拡張および停止の資本コストを指定する線形式を定義します。

### 必要な引数

`model` は、コストを指定するために追加しているシナリオツリー内のノードに対応するJuDGEサブ問題です。

`expr` は、現在のノードでの拡張および停止変数を選択することによる総コストを示す `AffExpr` です。

### 例

```
@capitalcosts(model, sum(expand[i]*cost[node][i] for i in 1:5))
```
