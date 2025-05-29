```
p4est_lid_copy(input, output)
```

初期化された [`p4est_lid_t`](@ref) を別の [`p4est_lid_t`](@ref) にコピーします。

### パラメータ

  * `input`:[in] コピーされる [`p4est_lid_t`](@ref) へのポインタ。
  * `output`:[in,out] [`p4est_lid_t`](@ref) へのポインタ。*output* の低ビットは *input* の低ビットに設定され、高ビットは無視されます。

### プロトタイプ

```c
void p4est_lid_copy (const p4est_lid_t * input, p4est_lid_t * output);
```
