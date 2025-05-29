```
p4est_connectivity_new_cubed()
```

単位立方体の6つの面のための接続構造を作成します。木の順序は次のとおりです: 0 1 2 3 <– 3: 軸に沿った上面 4 5。この選択は最大の対称性のために行われました（.cファイルのtree*to**を参照）。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_cubed (void);
```
