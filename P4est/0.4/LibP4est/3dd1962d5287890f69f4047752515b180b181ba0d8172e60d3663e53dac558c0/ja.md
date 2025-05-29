```
sc_array_permute(array, newindices, keepperm)
```

与えられた置換 *newindices* に基づいて、*array* をその場で置換します。入力時に *array*[i] に含まれるデータは、出力時には *array*[newindices[i]] に含まれます。*keepperm* が true でない限り、newindices のエントリは変更されます。

### パラメータ

  * `array`:[in,out] 配列。
  * `newindices`:[in,out] 置換配列（[`sc_array_is_permutation`](@ref) を参照）。
  * `keepperm`:[in] true の場合、*newindices* はアルゴリズムによって変更されません。false の場合、*newindices* は出力時に恒等置換になりますが、アルゴリズムは O(1) の空間しか使用しません。

### プロトタイプ

```c
void sc_array_permute (sc_array_t * array, sc_array_t * newindices, int keepperm);
```
