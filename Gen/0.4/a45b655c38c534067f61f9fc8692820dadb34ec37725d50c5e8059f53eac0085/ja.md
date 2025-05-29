```
choices::ChoiceMap = from_array(proto_choices::ChoiceMap, arr::Vector)
```

プロトタイプ割り当てと同じアドレス構造を持つ割り当てを返しますが、与えられた配列から読み取った値を使用します。

アドレスが埋められる順序はプロトタイプ割り当てによって決まります。プロトタイプ割り当ての選択肢の数が配列の長さと等しくない場合はエラーです。

# 実装

`from_array`をサポートするために、具体的なサブタイプ `T <: ChoiceMap` は以下のメソッドを実装する必要があります：

```
(n::Int, choices::T) = _from_array(proto_choices::T, arr::Vector{V}, start_idx::Int) where {V}
```

プロトタイプ割り当てと同じアドレス構造を持つ割り当てを返しますが、`arr`からの値を`start_idx`の位置から読み取り、`arr`から読み取る要素の数を指定します。
