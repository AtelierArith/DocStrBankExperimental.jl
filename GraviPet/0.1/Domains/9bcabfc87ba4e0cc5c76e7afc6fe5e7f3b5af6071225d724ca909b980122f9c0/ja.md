```
shifted(dom::Domain, shift)::Domain
```

ドメイン `dom` を同じ方向に両方のドメイン境界を移動させることでシフトします。これにより、ドメインのサイズは変わりません。

`shfited(dom, shift)` は `expanded(dom, -shift, +shift)` と同等です。

参照: [`expanded`](@ref).
