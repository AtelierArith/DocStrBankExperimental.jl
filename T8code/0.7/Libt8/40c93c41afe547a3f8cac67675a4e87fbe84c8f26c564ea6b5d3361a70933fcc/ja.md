```
t8_forest_ref(forest)
```

フォレストの参照カウンタを増加させます。

# 引数

  * `forest`:[in,out] 入力時、このフォレストは正の参照カウントで存在している必要があります。任意の状態である可能性があります。

### プロトタイプ

```c
void t8_forest_ref (t8_forest_t forest);
```
