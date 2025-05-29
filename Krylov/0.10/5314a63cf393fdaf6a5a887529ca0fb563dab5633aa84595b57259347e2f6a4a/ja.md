インプレースメソッド[`cg_lanczos_shift!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = CgLanczosShiftWorkspace(m, n, nshifts, S)
workspace = CgLanczosShiftWorkspace(A, b, nshifts)
workspace = CgLanczosShiftWorkspace(kc::KrylovConstructor, nshifts)
```
