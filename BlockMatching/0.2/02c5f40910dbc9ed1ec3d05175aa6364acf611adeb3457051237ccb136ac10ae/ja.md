```
FullSearch(d=Cityblock(), N; patch_radius, search_radius, search_stride=1)
```

フルサーチ戦略を用いたブロックマッチングアルゴリズムを構築します。一部の文献では、これを*徹底的検索*とも呼びます。

デフォルトのパッチ距離は`Distances.Cityblock()`です。

!!! note
    `p`が指定されておらず、入力が`CuArray`の場合、GPUメソッドがDistances.jlからの小さなセットの事前定義された距離に対して適用されます。結果はCPUバージョンとはわずかに異なります。

