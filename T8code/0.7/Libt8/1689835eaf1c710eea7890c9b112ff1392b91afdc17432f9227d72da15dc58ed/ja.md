```
t8_forest_set_partition(forest, set_from, set_for_coarsening)
```

コミット中にパーティション分割されるソースフォレストを設定します。パーティショニングはSFCに従って行われ、各ランクには同じ数（場合によっては+1）の要素が割り当てられます。

!!! note
    この設定はt8*forest*set*adaptおよびt8*forest*set*balanceと組み合わせることができます。これらの操作が実行される順序は常に1) 適応 2) バランス 3) パーティションです。t8*forest*set*balanceが*no*repartition*パラメータをfalseに設定して呼び出された場合、t8*forest*set_partitionを追加で呼び出す必要はありません。


!!! note
    この設定はt8*forest*set_copyと組み合わせることはできず、この設定を上書きします。


# 引数

  * `forest`:[in,out] フォレスト。
  * `set_from`:[in] パーティション分割されるべき第二のフォレスト。所有権を取得します。**set_from**を参照することでこれを防ぐことができます。NULLの場合、以前（または後で）設定されたフォレストが使用されます（t8*forest*set*adapt、t8*forest*set*balance）。
  * `set_for_coarsening`:[in] 現在無効。trueの場合、パーティションは要素を一度粗くすることがプロセスローカル操作となるように選択されます。

### プロトタイプ

```c
void t8_forest_set_partition (t8_forest_t forest, const t8_forest_t set_from, int set_for_coarsening);
```
