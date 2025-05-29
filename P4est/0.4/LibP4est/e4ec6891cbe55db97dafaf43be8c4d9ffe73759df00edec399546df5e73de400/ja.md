```
sc_array_is_permutation(array)
```

*array* が size*t の配列であり、そのエントリがすべての整数 0 <= i < array->elem*count を含むかどうかを判断します。

### パラメータ

  * `array`:[in] 配列。

### 戻り値

array が size*t 要素を含み、そのエントリがすべての整数 0 <= i < *array*->elem*count を含む場合は 1 を返し、それ以外の場合は 0 を返します。

### プロトタイプ

```c
int sc_array_is_permutation (sc_array_t * array);
```
