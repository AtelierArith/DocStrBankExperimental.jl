```
makematrix!(self::SysmatAssemblerSparseHRZLumpingSymm)
```

スパースHRZラプトされた**対称正方行列**を作成します。

!!! note
    `nomatrixresult`がtrueに設定されている場合、ダミー（ゼロ）スパース行列が返されます。アセンブリの全結果はアセンブラバッファに保持されます。バッファの端は不正（無視可能）な値で埋められます。


!!! note
    行列が構築されるとき（`nomatrixresult`がfalse）、バッファは解放されず、`buffer_pointer`は1に設定されます。これにより、別の行列のアセンブリをすぐに開始することが可能になります。

