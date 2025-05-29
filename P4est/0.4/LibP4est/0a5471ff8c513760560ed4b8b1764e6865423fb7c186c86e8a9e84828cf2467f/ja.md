```
sc_hash_array_rip(hash_array, rip)
```

ハッシュ配列から配列データを抽出し、他のすべてを破壊します。

### パラメータ

  * `hash_array`:[in] 抽出後、ハッシュ配列は破壊されます。
  * `rip`:[in] 上書きされる配列構造。すべての以前の配列データ（もしあれば）は漏洩します。埋められた配列は[`sc_array_reset`](@ref)で解放できます。

### プロトタイプ

```c
void sc_hash_array_rip (sc_hash_array_t * hash_array, sc_array_t * rip);
```
