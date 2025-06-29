acset内の部分に関連するスーパー部分を取得します。

サブ部分がインデックスされている場合、これは定数時間で行われます。そうでない場合は線形時間がかかります。[`subpart`](@ref)と同様に、単一およびベクトル化されたアクセス、ならびにチェーンアクセスがサポートされています。写像の列は通常の左から右への順序で提供されるため、

```
incident(g, x, [:src, :vattr])
```

は、ソース頂点が頂点属性`x`を持つすべてのエッジのリストを返します。

サブ部分のチェイニングがタプル（例：(:src, :vattr)）として与えられる場合、コード生成が使用されてサブ部分とその順序が有効な合成であることを確認し、パフォーマンスを向上させます。

サブ部分がインデックスされている場合、この関数は基礎となるインデックスのビューを返しますが、これは変更されるべきではありません。インデックスが有効かどうかに関わらず新しいコピーが返されることを保証するために、キーワード引数`copy=true`を設定してください。
