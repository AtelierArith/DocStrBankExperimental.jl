```
makematrix!(self::SysmatAssemblerSparseDiag)
```

スパース対称正方行列を作成します。

!!! note
    `nomatrixresult` が true に設定されている場合、ダミー（ゼロ）スパース行列が返されます。アセンブリの全結果はアセンブラバッファに保持されます。バッファの端は不正（無視可能）な値で埋められます。


!!! note
    行列が構築されるとき（`nomatrixresult` が false）、バッファは解放されず、`buffer_pointer` は 1 に設定されます。これにより、別の行列のアセンブリをすぐに開始することが可能になります。

