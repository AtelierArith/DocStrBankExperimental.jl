```
gfrefn(t1, t2, s1, s2)
```

状態変化をテストする次の時刻を見つけるために、より良い方法がない場合は二分法を使用します。

### 引数

  * `t1`: 状態変化を挟む2つの値の1つ
  * `t2`: 状態変化を挟むもう1つの値
  * `s1`: `t1`での状態
  * `s2`: `t2`での状態

### 出力

遷移をチェックするための新しい値を返します。

### 参考文献

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/gfrefn_c.html)
