```
kernelproduct(hood::AbstractKernelStencil)
kernelproduct(hood::Stencil, kernel)
```

ステンシルとカーネルのベクトルドット積を返しますが、`dot`とは異なり、ステンシルのメンバーに対して反復的に計算されるのではなく、スカラーとして扱われます。
