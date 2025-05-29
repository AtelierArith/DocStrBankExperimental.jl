```
dilate!(Amax, A, B=3; order=FORWARD_FILTER, slow=false) -> Amax
```

は、配列 `A` の膨張を構造要素 `B` によって定義し、`Amax` を上書きして返します。

キーワード `order` はフィルタの方向を指定し、デフォルトでは `FORWARD_FILTER` です。

構造要素 `B` が単純なハイパー長方形のスライディングウィンドウに相当する場合（デフォルトではその通り）で、キーワード `slow` が true でない限り、はるかに高速な van Herk-Gil-Werman アルゴリズムが使用され、操作はインプレースで行うことができます。つまり、`A` と `Amin` は同じ配列であることができます。その場合、次の構文が許可されます：

```
dilate!(A, B=3; order=FORWARD_FILTER) -> A
```

詳細およびアウトオブプレースバージョンについては、[`dilate`](@ref) を参照してください。
