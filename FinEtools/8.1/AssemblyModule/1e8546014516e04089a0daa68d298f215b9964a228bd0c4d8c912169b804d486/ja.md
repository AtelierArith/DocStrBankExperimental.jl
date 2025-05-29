```
makematrix!(self::SysmatAssemblerSparse)
```

スパース行列を作成します。

スパース行列が返されます。

!!! note
    `nomatrixresult`がtrueに設定されている場合、ダミー（ゼロ）スパース行列が返されます。アセンブリの全結果はアセンブラバッファに保持されます。バッファの端は不正（無視可能）な値で埋められます。


!!! note
    行列が構築されるとき（`nomatrixresult`がfalse）、バッファは解放されず、`buffer_pointer`は1に設定されます。これにより、すぐに別の行列のアセンブリを開始することが可能になります。

