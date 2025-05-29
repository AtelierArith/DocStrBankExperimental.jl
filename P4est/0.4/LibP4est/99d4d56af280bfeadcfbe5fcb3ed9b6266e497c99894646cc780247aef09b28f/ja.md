```
p4est_connectivity_new_disk_nonperiodic()
```

五木の平坦な球面ディスクの接続構造を作成します。このディスクは、非カルテジアンマップをテストするために正方形としても使用できます。マッピングなしで、この接続は正方形 [-3, 3]**2 をカバーします。

### 戻り値

初期化され、使用可能な接続。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_disk_nonperiodic (void);
```
