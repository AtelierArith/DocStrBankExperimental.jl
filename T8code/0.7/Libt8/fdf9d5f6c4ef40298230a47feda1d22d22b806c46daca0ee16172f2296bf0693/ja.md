```
t8_forest_set_balance(forest, set_from, no_repartition)
```

コミット中にソースフォレストをバランスさせる。フォレストは、各要素がその要素のレベルの±1のレベルを持つ面の隣接要素を持つ場合、バランスが取れていると言われる。

!!! note
    この設定は、t8*forest*set*adaptおよびt8*forest*set*balanceと組み合わせることができます。これらの操作が実行される順序は常に1) 適応 2) バランス 3) パーティションです。


!!! note
    この設定は、t8*forest*set_copyと組み合わせることはできず、この設定を上書きします。


# 引数

  * `forest`:[in,out] フォレスト。
  * `set_from`:[in] バランスを取るべき第二のフォレスト。所有権を取得します。これは**set_from**を参照することで防ぐことができます。NULLの場合、以前（または後に）設定されたフォレストが取られます（t8*forest*set*adapt、t8*forest*set*partition）。
  * `no_repartition`:[in] バランスは、互いに洗練された複数の中間フォレストを構築します。バランスの取れた負荷を維持するために、これらのフォレストは各ラウンドで再パーティションされ、結果として得られるフォレストはデフォルトで負荷バランスが取れています。この動作が望ましくない場合は、*no_repartition*をtrueに設定する必要があります。*no_repartition*がfalseの場合、t8*forest*set_partitionの追加呼び出しは必要ありません。

### プロトタイプ

```c
void t8_forest_set_balance (t8_forest_t forest, const t8_forest_t set_from, int no_repartition);
```
