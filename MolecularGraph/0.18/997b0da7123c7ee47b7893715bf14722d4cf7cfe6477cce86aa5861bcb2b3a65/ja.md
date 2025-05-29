```
safe_stereo_hydrogen!(mol::SimpleMolGraph, v::Integer) -> Bool
```

ステレオセンターのプロパティを再配置して、ステレオ水素ノードを安全に削除し、水素ノードのインデックスを返します。

この関数は、ステレオセンター情報を保持しながら水素ノードを安全に削除するために、`rem_vertex!`および`rem_vertices!`関数内で呼び出されます。
