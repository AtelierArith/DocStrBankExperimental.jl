```
launch(f::CuFunction; args...; blocks::CuDim=1, threads::CuDim=1,
       cooperative=false, shmem=0, stream=stream())
```

GPU上でCUDA関数`f`を起動するための低レベルの呼び出しであり、`blocks`と`threads`をそれぞれグリッドとブロックの構成として使用します。動的共有メモリは`shmem`に従って割り当てられ、カーネルはストリーム`stream`で起動されます。

カーネルへの引数は、ビットタイプである必要があり、その場合は内部カーネルパラメータバッファにコピーされるか、デバイスメモリへのポインタである必要があります。

これは低レベルの呼び出しであり、代わりに[`cudacall`](@ref)を使用することをお勧めします。
