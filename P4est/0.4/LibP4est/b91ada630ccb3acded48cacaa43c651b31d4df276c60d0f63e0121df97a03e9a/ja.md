```
p8est_checksum_partition(p8est_)
```

フォレストのパーティション依存のチェックサムを計算します。

### 戻り値

プロセッサ0のみでチェックサムを返します。他のプロセッサでは0を返します。

### プロトタイプ

```c
unsigned p8est_checksum_partition (p8est_t * p8est);
```
