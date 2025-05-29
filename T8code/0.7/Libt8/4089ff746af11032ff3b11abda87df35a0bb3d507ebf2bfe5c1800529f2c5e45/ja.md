```
t8_cmesh_trees_finish_part(trees, proc)
```

すべての木とゴーストのクラスが設定され、木の属性の数が設定され、その合計サイズ（木ごと）が一時的に att_offset 変数に保存された後、必要なメモリ量だけ部分配列を成長させ、オフセットを適切に設定します。ワークフローは次のようになります：t8*cmesh*trees*start*part を呼び出し、t8*cmesh*trees*add*tree および t8*cmesh*trees*add*ghost を介して手動で木とゴーストのクラスを設定し、t8*cmesh*trees*init*attributes を呼び出し、その後この関数を呼び出します。その後、各属性に対して t8*cmesh*trees*add*attribute を順次呼び出し、すべての面の隣接を設定します（TODO: 関数を書く）。

# 引数

  * `trees`:[in,out] 更新される木の構造体。
  * `proc`:[in] 完了する部分の番号。

### プロトタイプ

```c
void t8_cmesh_trees_finish_part (t8_cmesh_trees_t trees, int proc);
```
