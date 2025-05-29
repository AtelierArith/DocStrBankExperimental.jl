```
t8_cmesh_destroy(pcmesh)
```

粗いメッシュに参照が1つだけ残っていることを確認し、それを破棄します。この関数は、最後の参照が削除されることがわかっている場合に、t8*cmesh*unrefよりも好まれます。

# 引数

  * `pcmesh`:[in,out] このcmeshは参照カウントが1でなければなりません。任意の状態（コミット済みまたは未コミット）であることができます。その後、実質的にt8*cmesh*unrefを呼び出します。
  * `comm`:[in] *cmesh*に対して有効なmpiコミュニケーター。

### プロトタイプ

```c
void t8_cmesh_destroy (t8_cmesh_t *pcmesh);
```
