```
t8_cmesh_init(pcmesh)
```

新しいcmeshを参照カウント1で作成します。このcmeshは、t8*cmesh*set_*呼び出しで特化する必要があります。その後、t8*cmesh*commitでセットアップする必要があります。

# 引数

  * `pcmesh`:[in,out] 入力時、このポインタはNULLであってはなりません。戻り値として、このポインタは新しいcmeshに設定されます。

### プロトタイプ

```c
void t8_cmesh_init (t8_cmesh_t *pcmesh);
```
