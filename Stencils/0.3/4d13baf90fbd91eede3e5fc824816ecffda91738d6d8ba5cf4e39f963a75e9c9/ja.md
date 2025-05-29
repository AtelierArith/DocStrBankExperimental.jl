```
mapstencil!(f, dest::AbstractArray, source::StencilArray, args::AbstractArray...)
mapstencil!(f, A::SwitchingStencilArray, args::AbstractArray...)
```

スタンシルマッピングでは、`f` が `src` の各インデックスで中心にあるスタンシルと、各スタンシル中心での `args` の値を受け取ります。`f` の結果は `dest` に書き込まれます。

`SwitchingStencilArray` の場合、内部のソースおよびデスティネーション配列が使用され、配列のスイッチされたバージョンが返されます。

`dest` は、すべての側でスタンシル半径分 `src` より小さいか、同じサイズである必要があり、その場合はパディングされていると見なされます。
