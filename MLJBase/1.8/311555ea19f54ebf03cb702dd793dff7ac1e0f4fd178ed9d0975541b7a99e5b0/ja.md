```
glb(N1, N2, ...)
```

与えられたノード `N1`, `N2`, ... に基づいて、振る舞い `N() = (N1(), N2(), ...)` を持つノード `N` を構築します。つまり、`glb` はノードに対してオーバーロードされた `tuple` です。

`@tuple N1 N2 ...` と同等です。
