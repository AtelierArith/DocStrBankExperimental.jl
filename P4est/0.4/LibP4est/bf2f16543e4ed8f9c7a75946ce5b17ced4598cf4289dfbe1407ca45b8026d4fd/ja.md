```
p4est_connectivity_new_disk(periodic_a, periodic_b)
```

五木の平坦な球面ディスクの接続構造を作成します。このディスクは、非直交マップをテストするために正方形としても使用できます。マッピングなしで、この接続は正方形 [-3, 3]**2 をカバーします。

!!! note
    この関数のAPIは、2つの引数を受け入れるように変更されました。新しいバージョンが引数を受け入れているかどうかを確認するには、#define `P4EST_CONN_DISK_PERIODIC` を照会できます。


木の順序は次のとおりです: 4 1 2 3 0。

外側のx面は位相的に同一視される場合があります。外側のy面は位相的に同一視される場合があります。両方の同一視は同時に指定できます。一般的な形状と周期性は、p4est*connectivity*new*brick (1, 1, periodic\*a, periodic_b) で得られるものと同じです。

*periodic_a* と *periodic_b* を false に設定すると、結果は p4est*connectivity*new*disk*nonperiodic のものと同じになります。

### パラメータ

  * `periodic_a`:[in] ディスクをx方向に周期的にするためのBool。
  * `periodic_b`:[in] ディスクをy方向に周期的にするためのBool。

### 戻り値

初期化され、使用可能な接続。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_disk (int periodic_a, int periodic_b);
```
