```
DEMSystem(initial_condition, contact_model; damping_coefficient=0.0001,
          acceleration=ntuple(_ -> 0.0, ndims(initial_condition)), source_terms=nothing,
          radius=nothing)
```

離散要素法（DEM）システムを構築し、粒状および粒子状物質の動力学を数値的にシミュレーションします。DEMは、通常、機械的負荷の下で、離散的な固体粒子の集合体の運動、相互作用、および集合的な挙動をシミュレートおよび分析するために使用されます。このモデルは、個々の粒子の特性を考慮し、指定された材料特性および接触力学に基づいて接触力（法線および接線）を支配する相互作用法則を実装します。

# 引数

  * `initial_condition`: システムの初期条件で、粒子の初期位置、速度、質量、および半径をカプセル化します。
  * `contact_model`: 粒子相互作用に使用される接触モデル。

# キーワード

  * `acceleration`: 重力など、システムに適用されるグローバル加速度ベクトル。`NDIMS`の長さの`SVector`として指定され、各次元でのデフォルトはゼロです。
  * `source_terms`: オプション; 標準のDEM相互作用では捉えられない粒子の動力学に対する追加の力や修正、例えば電磁力やユーザー定義の摂動など。
  * `damping_coefficient=0.0001`: 衝突相互作用のための減衰係数を設定します。
  * `radius=nothing`: 粒子の半径を指定し、デフォルトは`initial_condition.particle_spacing / 2`です。

!!! warning "実験的実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

[Bicanic2004](@cite), [Cundall1979](@cite), [DiRenzo2004](@cite)
