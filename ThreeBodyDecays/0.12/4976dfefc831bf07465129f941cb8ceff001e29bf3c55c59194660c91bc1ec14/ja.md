```
DecayChainLS(; k, Xlineshape, jp, Ps, tbs)
```

最小スピン-軌道結合を持つ崩壊鎖を構築します。

# 引数

  * `k`: スペクトレーター粒子のインデックス。
  * `Xlineshape`: 共鳴のラインシェイプのためのラムダ関数。
  * `jp`: 共鳴のスピン-パリティ（例: `jp = "1/2-"`）。
  * `Ps`: 三体系のパリティ（例: `Ps = ThreeBodyParities('+','+','+'; P0='+')`）。
  * `tbs`: 三体系の構造。

# 例

```julia
DecayChainLS(     
    k = 1,     
    Xlineshape = x -> 1 / (x - 1im),     
    jp = "1/2-",     
    Ps = ThreeBodyParities('+', '+', '+'; P0 = '+'),     
    tbs = ThreeBodySystem(1.0, 2.0, 3.0; m0 = 4.0) 
)
```
