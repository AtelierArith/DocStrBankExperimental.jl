インプレースメソッド[`cgls_lanczos_shift!`](@ref)のためのワークスペース。

以下の外部コンストラクタを使用して、このワークスペースを初期化できます::

```
workspace = CglsLanczosShiftWorkspace(m, n, nshifts, S)
workspace = CglsLanczosShiftWorkspace(A, b, nshifts)
workspace = CglsLanczosShiftWorkspace(kc::KrylovConstructor, nshifts)
```
