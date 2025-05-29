```
extract_attractors(mapper::AttractorsMapper) → attractors
```

`mapper`によって見つかったアトラクターにラベルIDをマッピングする辞書を返します。この関数は、アトラクターが実際に最初に見つかるように、与えられた`mapper`で[`basins_fractions`](@ref)を呼び出した後に呼び出す必要があります。

`AttractorsViaFeaturizing`の場合、アトラクターは、サンプラー（初期条件を返す関数）ではなく、事前に定義された初期条件で`mapper`が呼び出された場合にのみ保存されます。
