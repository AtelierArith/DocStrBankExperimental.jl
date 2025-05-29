```
sc_array_is_equal(array, other)
```

2つの配列が同じサイズ、カウント、および内容を持っているかどうかを確認します。どちらの配列もビューである可能性があります。両方の配列は変更されません。

### パラメータ

  * `array`:[in] 比較される1つの配列。
  * `other`:[in] 比較される2つ目の配列。

### 戻り値

arrayとotherが等しい場合は真、そうでない場合は偽。

### プロトタイプ

```c
int sc_array_is_equal (sc_array_t * array, sc_array_t * other);
```
