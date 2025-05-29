```
arr::Vector{T} = to_array(choices::ChoiceMap, ::Type{T}) where {T}
```

与えられた割り当ての値で配列を埋めます。

各値を指定された型の値に強制変換できない場合はエラーです。

# 実装

`to_array`をサポートするために、具体的なサブタイプ`T <: ChoiceMap`は次のメソッドを実装する必要があります。

```
n::Int = _fill_array!(choices::T, arr::Vector{V}, start_idx::Int) where {V}
```

与えられた割り当てからの値で`arr`を埋め、`start_idx`から始め、`arr`に埋められた要素の数を返します。
