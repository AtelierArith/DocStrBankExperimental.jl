```
t8_forest_is_equal(forest_a, forest_b)
```

2つのコミットされたフォレストが同じローカル要素を持っているかどうかを確認します。

!!! note
    この関数は集団的ではありません。現在のランクの状態のみを返します。


# 引数

  * `forest_a`:[in] 最初のフォレスト。
  * `forest_b`:[in] 2番目のフォレスト。

# 戻り値

*forest_a* と *forest_b* が同じ数のローカルツリーを持ち、各ローカルツリーが同じ要素を持っている場合、すなわち *forest_a* と *forest_b* の各要素のペアに対して t8*element*equal が true を返す場合に真を返します。

### プロトタイプ

```c
int t8_forest_is_equal (t8_forest_t forest_a, t8_forest_t forest_b);
```
