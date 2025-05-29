```
distmesh
符号距離関数を使用した3Dメッシュジェネレーター。
引数:
    fdist:       距離関数
    fh:          辺の長さ関数
    h:           最小辺の長さ

返り値:
    p:           ノードの位置
    t:           三角形のインデックス


例: 単位球
    d(p) = sqrt(sum(p.^2))-1
    p,t = distmeshnd(d,huniform,0.2)
```
