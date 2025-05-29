```
p4est_checksum_partition(p4est_)
```

フォレストに対するパーティション依存のチェックサムを計算します。

### 戻り値

プロセッサ0のみでチェックサムを返します。他のプロセッサでは0を返します。

### プロトタイプ

```c
unsigned p4est_checksum_partition (p4est_t * p4est);
```
