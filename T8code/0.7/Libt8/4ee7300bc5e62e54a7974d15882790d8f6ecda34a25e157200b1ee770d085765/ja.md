```
t8_forest_init(pforest)
```

新しいフォレストを参照カウント1で作成します。このフォレストは、t8*forest*set_* 呼び出しで特化する必要があります。現在、t8*forest*set*mpicomm、t8*forest*set*cmesh、および t8*forest*set*scheme のいずれかの関数を呼び出すか、t8*forest*set*copy、t8*forest*set*adapt、または t8*forest*set*partition のいずれかを呼び出すことが必須です。これらの呼び出しを混在させたり、後者の3つの関数のうちの1つ以上を呼び出すことは違法です。その後、t8*forest*commit で設定する必要があります。

# 引数

  * `pforest`:[in,out] 入力時、このポインタはNULLであってはなりません。戻り値として、このポインタは新しいフォレストに設定されます。

### プロトタイプ

```c
void t8_forest_init (t8_forest_t *pforest);
```
