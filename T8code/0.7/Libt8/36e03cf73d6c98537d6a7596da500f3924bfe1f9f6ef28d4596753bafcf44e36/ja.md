```
t8_stash_is_equal(stash_a, stash_b)
```

2つのスタッシュの内容が等しいかを確認し、そうであればtrueを返します。

# 引数

  * `stash_a`:[in] 考慮される最初のスタッシュ。
  * `stash_b`:[in] 考慮される2番目のスタッシュ。

# 戻り値

両方のスタッシュが同じデータのコピーを保持している場合はTrue。そうでない場合はFalse。

### プロトタイプ

```c
int t8_stash_is_equal (t8_stash_t stash_a, t8_stash_t stash_b);
```
