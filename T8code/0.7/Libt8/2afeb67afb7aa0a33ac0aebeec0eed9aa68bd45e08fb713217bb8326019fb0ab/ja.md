```
t8_cmesh_ref(cmesh)
```

cmeshの参照カウンタを増加させます。

# 引数

  * `cmesh`:[in,out] 入力時、このcmeshは正の参照カウントで存在している必要があります。任意の状態である可能性があります。

### プロトタイプ

```c
void t8_cmesh_ref (t8_cmesh_t cmesh);
```
