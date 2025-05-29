```
sc_array_resize(array, new_count)
```

要素数を new*count に設定します。配列がビューでない場合、再割り当てが時折行われます。配列がビューである場合、new*count はビューが作成されたときの要素数を超えてはいけません。ビューの元のオフセットは変更できません。

### パラメータ

  * `array`:[in,out] 要素数とアドレスが変更されます。
  * `new_count`:[in] 配列の新しい要素数。ゼロであり、配列がビューでない場合、その効果は sc*array*reset と等しくなります。

### プロトタイプ

```c
void sc_array_resize (sc_array_t * array, size_t new_count);
```
