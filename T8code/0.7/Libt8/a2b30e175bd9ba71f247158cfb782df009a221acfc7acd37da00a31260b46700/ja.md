```
t8_cmesh_is_equal(cmesh_a, cmesh_b)
```

2つの与えられたcmeshが同じ情報を持っているかどうかを確認します。

# 引数

  * `cmesh_a`:[in] チェックされる2つのcmeshのうちの最初のもの。
  * `cmesh_b`:[in] チェックされる2つのcmeshのうちの2番目のもの。

# 戻り値

両方のcmeshが同じ情報を持っている場合は真、そうでない場合は偽。TODO: 注意深く定義する。順序、シーケンス、同等性？この関数はコミットされたcmeshとコミットされていないcmeshの両方で動作します。

### プロトタイプ

```c
int t8_cmesh_is_equal (t8_cmesh_t cmesh_a, t8_cmesh_t cmesh_b);
```
