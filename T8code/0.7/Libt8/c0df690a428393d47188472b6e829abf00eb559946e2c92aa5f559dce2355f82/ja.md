```
t8_forest_set_level(forest, level)
```

**forest** がコミットされるときに使用される初期の細分化レベルを設定します。

!!! note
    この設定は、派生した森林メソッド（t8*forest*set*copy、t8*forest*set*adapt、t8*forest*set*partition、および t8*forest*set*balance）と組み合わせることはできず、これらの設定を上書きします。この関数が使用されると、森林は指定された cmesh（t8*forest*set*cmesh、t8*forest*set*scheme）の均一な細分化からゼロから作成されます。


# 引数

  * `forest`:[in,out] レベルが設定される森林。
  * `level`:[in] **forest** の初期細分化レベル、コミットされるとき。

### プロトタイプ

```c
void t8_forest_set_level (t8_forest_t forest, int level);
```
