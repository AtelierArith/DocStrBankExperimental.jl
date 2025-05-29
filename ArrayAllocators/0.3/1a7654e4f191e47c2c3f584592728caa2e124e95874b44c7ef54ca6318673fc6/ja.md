```
MallocAllocator()
```

配列を[`Libc.malloc`](https://docs.julialang.org/en/v1/base/libc/#Base.Libc.malloc)を使用して割り当てます。これは有用であることを目的としたものではなく、カスタム配列アロケータの概念をプロトタイプするためのものです。これは`undef`を使用するのと似ています。

詳細はhttps://en.cppreference.com/w/c/memory/mallocをご覧ください。
