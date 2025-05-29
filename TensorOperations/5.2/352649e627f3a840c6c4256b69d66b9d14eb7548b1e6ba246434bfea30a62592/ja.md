```
@cutensor tensor_expr
```

GPUを使用して、cuTENSORライブラリを通じてすべてのテンソル操作を実行します。これにより、要求された操作を実行する前にすべての配列がGPUに転送されます。出力が既存のホスト配列である場合、結果は戻されます。新しい配列が作成される場合（つまり、`:=`を使用する場合）、それはGPUデバイス上に残り、ユーザーがそれを戻す責任があります。このマクロは、`@tensor backend=cuTENSORBackend() allocator=CUDAAllocator() tensor_expr`と同等です。

!!! note
    このマクロは、cuTENSORライブラリがインストールされ、ロードされていることを要求します。これは、マクロを使用する前に`using cuTENSOR`または`import cuTENSOR`を実行することで達成できます。

