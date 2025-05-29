```
writesubtree!(IO, network, dendroscope::Bool, namelabel::Bool,
              round_branch_lengths::Bool, digits::Integer,
              internallabel::Bool)
```

IOにネットワークの拡張ニューイック形式（括弧付き記述）を書き込みます。dendroscope用に書かれている場合、継承γは書かれません。`namelabel`がtrueの場合、分類群はその名前でラベル付けされます。そうでない場合、分類群はその番号IDでラベル付けされます。指定されていない場合、枝の長さとγは3桁に丸められます。内部ノードのラベルを抑制するには`internallabel=false`を使用します。
