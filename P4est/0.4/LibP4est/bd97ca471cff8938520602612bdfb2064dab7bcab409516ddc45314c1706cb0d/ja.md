```
sc_recycle_array_reset(rec_array)
```

リサイクル配列をリセットします。

すべての *reset 関数と同様に、*init を呼び出し、その後に任意の配列操作を行い、最後に _reset を呼び出すことはメモリに中立です。

### プロトタイプ

```c
void sc_recycle_array_reset (sc_recycle_array_t * rec_array);
```
