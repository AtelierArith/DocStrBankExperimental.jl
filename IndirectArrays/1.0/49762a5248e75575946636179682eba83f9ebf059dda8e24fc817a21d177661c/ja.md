```
IndirectArray(index, values)
```

は、`index`を使用して値テーブル`values`から値を検索する配列`A`を作成します。具体的には、`A[i...] = values[index[i...]]`です。

`values`は、`index`の値が連続している場合に便利な`AbstractVector`または、そうでない場合に便利な`AbstractDict`であることができます。あまり多くない異なる値がある場合は、パフォーマンスのために[OrderedCollections](https://github.com/JuliaCollections/OrderedCollections.jl)の「凍結された」LittleDictを推奨します。
