```
gaspi_state_vec_get(state_vector)
```

状態ベクターを取得します。

### パラメータ

  * `state_vector`: 各ランクの状態を持つベクター。ベクターはすべてのランクの状態を保持するのに十分な場所を確保している必要があります。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_state_vec_get (gaspi_state_vector_t state_vector);
```
