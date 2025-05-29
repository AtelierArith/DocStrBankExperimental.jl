```
condition_mutation_weights!(weights::AbstractMutationWeights, member::PopMember, options::AbstractOptions, curmaxsize::Int)
```

現在のメンバーとオプションの特性に基づいて突然変異の重みを調整します。

この関数は、メンバーに適用される突然変異がその現在の状態と提供されたオプションに対して適切であることを保証するために、突然変異の重みを修正します。異なるタイプの式やメンバーに対して動作をカスタマイズするためにオーバーロードすることができます。

重みはすでにコピーされているため、突然変異について心配する必要はありません。

# 引数

  * `weights::AbstractMutationWeights`: 調整される突然変異の重み。
  * `member::PopMember`: 突然変異が行われている現在の集団メンバー。
  * `options::AbstractOptions`: 突然変異プロセスを導くオプション。
  * `curmaxsize::Int`: メンバーの式ツリーに対する現在の最大サイズ制約。
