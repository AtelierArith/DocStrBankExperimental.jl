```
table(columntable; prototype=nothing)
```

名前付きタプルのベクトルまたはタプル `columntable` を、`prototype` の「好ましいシンクタイプ」のテーブルに変換します。これは、`prototype` がシンクである場合、しばしば `prototype` 自体のタイプになります。Tables.jl のドキュメントを参照してください。`prototype` が指定されていない場合、ベクトルの名前付きタプルが返されます。

```
table(A::AbstractMatrix; names=nothing, prototype=nothing)
```

抽象行列 `A` を、指定された列 `names`（シンボルのタプル）を持つ Tables.jl 互換のテーブルとしてラップします。`names` が指定されていない場合、`names=(:x1, :x2, ..., :xn)` が使用され、ここで `n=size(A, 2)` です。

`prototype` が指定されている場合、行列はラップされるのではなく、`prototype` の好ましいシンクタイプのテーブルとして具現化されます。`prototype` が *指定されていない* 場合、`matrix(table(A))` は本質的に何もしない操作です。
