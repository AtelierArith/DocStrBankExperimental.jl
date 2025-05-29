```
EmbeddedManifoldObjective{P, T, E, O2, O1<:AbstractManifoldObjective{E}} <:
   AbstractDecoratedManifoldObjective{E,O2}
```

埋め込み内で定義される目的を宣言します。これにより、勾配も埋め込み内で定義され、特に埋め込み内のメトリックに関するリース表現者であることが宣言されます。型は、装飾されていない目的型 `O2` にもディスパッチするために使用できます。

# フィールド

  * `objective`: 埋め込み内で定義される目的
  * `p=nothing`: 埋め込み内の点。
  * `X=nothing`: 埋め込み内の接ベクトル

埋め込み内の点 `p` が提供されると、メモリ割り当てを減らすためにこの点の代わりに `embed!` が使用されます。同様に、接ベクトルを埋め込むときに `X` が使用されます。
