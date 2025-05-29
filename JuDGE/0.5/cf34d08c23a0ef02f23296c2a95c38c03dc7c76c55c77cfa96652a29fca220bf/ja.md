```
ongoingcosts(model, expr)
```

現在のノードで利用可能な拡張およびシャットダウンの継続的コストを指定する線形式を定義します。

### 必要な引数

`model` は、コストを指定するために追加しているシナリオツリー内のノードに対応するJuDGEサブ問題です。

`expr` は、現在のノードで利用可能な拡張およびシャットダウンの継続的コストを与える `AffExpr` です。

### 例

```
@ongoingcosts(model, sum(expand[i]*ongoingcosts[node][i] for i in 1:5))
```
