```
p8est_connectivity_is_equivalent(conn1, conn2)
```

[`p8est_connectivity_is_equivalent`](@ref) この関数は、2つの接続性を同等性のために比較します：それらが同じ接続性である場合、または同じトポロジーを持つ場合は*true*を返します。トポロジーの同一性の定義は厳密です：接続性を同等にするために木の順列や回転を判断しようとはしません。

### パラメータ

  * `conn1`:[in] 有効な接続性
  * `conn2`:[out] 有効な接続性

### プロトタイプ

```c
int p8est_connectivity_is_equivalent (p8est_connectivity_t * conn1, p8est_connectivity_t * conn2);
```
