```
DecayChainsLS(; k, Xlineshape, jp, Ps, tbs)
```

指定されたパラメータに基づいて、すべての可能な結合を持つ崩壊系列を生成します。

# 引数

  * `k`: 崩壊系列を指定する観測者のインデックス。
  * `Xlineshape`: 共鳴のラインシェイプのためのラムダ関数。
  * `jp`: 共鳴のスピン-パリティ量子数（例: `jp = "1/2-"`）。
  * `Ps`: 三体系のパリティ量子数（例: `Ps = ThreeBodyParities('+','+','+'; P0='+')`）。
  * `tbs`: 関与する粒子とその特性を定義する三体系の構造。

# 戻り値

  * 与えられた崩壊構成に対するすべての可能な結合を表す `DecayChain` オブジェクトの配列。

# 注意事項

この関数は、可能な結合の組み合わせ（`ls` x `LS`）を計算します。各組み合わせについて、適切な再結合項（`Hij`、`HRk`）を持つ `DecayChain` オブジェクトが作成されます。

# 例

```julia DecayChainsLS(     k=3, Xlineshape=σ->1.0, jp="1/2-", Ps=ThreeBodyParities('+','+','+'; P0='+'),     tbs=ThreeBodySystem(         ThreeBodyMasses(1, 2, 3; m0=7.0),         ThreeBodySpins(1, 2, 0; h0=3)     ) )

```
