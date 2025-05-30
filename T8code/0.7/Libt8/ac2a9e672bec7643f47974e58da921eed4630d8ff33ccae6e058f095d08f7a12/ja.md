```
t8_cmesh_set_partition_range(cmesh, set_face_knowledge, first_local_tree, last_local_tree)
```

cmeshが分割されたcmeshとして理解され、プロセッサのローカルツリー範囲を指定します。この関数は、cmeshが別のcmeshから派生していない場合、t8*cmesh*set*partition*offsetsよりも優先されるべきです。この呼び出しは、cmeshがまだt8*cmesh*commitへの呼び出しを介してコミットされていない場合にのみ有効です。

!!! note
    *set*face*knowledge*の値が-1または3以外はまだサポートされていません。


# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `set_face_knowledge`:[in] t8*cmesh*set*joinによって指定された、面接続に関して必要な情報の量を定義するいくつかの値が可能です。0: ローカルツリーの面接続を期待します。1: さらに、ゴーストツリーからローカルツリーへの面接続を期待します。2: さらに、ゴーストツリー間の面接続を期待します。3: ローカルツリーとゴーストツリーの面接続を期待します。この要件の整合性はt8*cmesh*commitでチェックされます。-1: face*knowledgeレベルを変更せず、以前に設定されたものを保持します。（おそらくt8*cmesh*set*partition*rangeへの以前の呼び出しによって）
  * `first_local_tree`:[in] このプロセスの最初のツリーのグローバルインデックスID。このツリーが前のプロセスの最後のツリーでもある場合、引数は-ID - 1でなければなりません。
  * `last_local_tree`:[in] このプロセスの最後のツリーのグローバルインデックス。このプロセスが空であるべき場合、*last*local*tree*は*first*local*tree*よりも厳密に小さくなければなりません。

# 参照

t8*cmesh*set*partition*offset, [`t8_cmesh_set_partition_uniform`](@ref)

### プロトタイプ

```c
void t8_cmesh_set_partition_range (t8_cmesh_t cmesh, int set_face_knowledge, t8_gloidx_t first_local_tree, t8_gloidx_t last_local_tree);
```
