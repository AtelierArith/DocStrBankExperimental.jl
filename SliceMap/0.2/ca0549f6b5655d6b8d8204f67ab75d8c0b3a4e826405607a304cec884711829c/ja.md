```
slicemap(f, A; dims) ≈ mapslices(f, A; dims)
```

`mapcols()`と同様ですが、任意のスライスに対して使用します。関数`f`は形状を保持する必要があります。例えば、`dims=(2,4)`の場合、`f`は行列を行列にマッピングする必要があります。

勾配はZygote専用です。

関数`f`内のパラメータ（もしあれば）は正しく追跡されるべきであり、これは`mapcols()`ではそうではありません。キーワード`rev=true`は`f`を`Iterators.reverse(Slices(A,...))`に適用し、逆の順序で反復します。
