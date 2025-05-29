```
kernelproduct(hood::AbstractKernelStencil)
kernelproduct(hood::Stencil, kernel)
```

ステンシルとカーネルのベクトルドット積を計算しますが、いずれの値にも再帰的に入ることはありません。基本的には、内容に対して再帰的な呼び出しを行わない `Base.dot` のようなものです。これは、通常意図されているものではありません。
