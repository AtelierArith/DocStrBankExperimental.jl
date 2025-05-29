```
one_topology(itr::InterpenetratedTopologyResult, clustering::Union{Nothing,_Clustering}=nothing)
```

与えられたクラスタリングに対応する唯一のトポロジーを返します。クラスタリングが指定されていない場合は、結果の唯一のトポロジーを返します。

複数のトポロジーが見つかった場合は、`nothing`を返します。

クラスタリングが相互浸透トポロジーのいずれかに見つからない場合は、`missing`を返します。
