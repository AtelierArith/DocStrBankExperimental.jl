```
create_sim(mesh; args...)
```

与えられた引数でマイクロ磁気シミュレーションインスタンスを作成します。

  * `mesh`: シミュレーションを開始するにはメッシュを提供する必要があります。メッシュは [`FDMesh`](@ref)、[`CubicMesh`](@ref)、または [`TriangularMesh`](@ref) である必要があります。

# 引数

  * `name` : シミュレーション名、文字列である必要があります。
  * `driver` : ドライバ名、文字列である必要があります。デフォルトでは、ドライバは "SD" です。
  * `alpha` : LLG 方程式におけるギルバート減衰、数値である必要があります。
  * `beta` : スピン移動トルクを伴う LLG 方程式における非断熱強度（zhang-li モデル）、数値である必要があります。
  * `gamma` : ジロマグネティック比、デフォルト値 = 2.21e5。
  * `ux`, `uy` または `uz`: スピン移動トルクの強度。
  * `ufun` : `u` の時間依存関数。
  * `Ms`: 飽和磁化、[`NumberOrArrayOrFunction`](@ref) である必要があります。デフォルトでは、Ms=8e5。
  * `mu_s`: 磁気モーメント、[`NumberOrArrayOrFunction`](@ref) である必要があります。デフォルトでは、mu*s=2*mu*B。
  * `A` または `J`: 交換定数、[`NumberOrArrayOrFunction`](@ref) である必要があります。
  * `D` : DMI 定数、[`NumberOrArrayOrFunction`](@ref) である必要があります。
  * `dmi_type` : DMI のタイプ、"bulk"、"interfacial" または "D2d" である可能性があります。
  * `Ku`: 異方性定数、[`NumberOrArrayOrFunction`](@ref) である必要があります。
  * `axis`: 異方性軸、タプルである必要があります。例: (0,0, 1)
  * `Kc`: 立方体異方性定数、[`NumberOrArrayOrFunction`](@ref) である必要があります。
  * `axis1`: 立方体異方性軸1、タプルである必要があります。例: (1,0,0)
  * `axis2`: 立方体異方性軸2、タプルである必要があります。例: (0,1,0)
  * `demag` : 磁化除去を含めるかどうか、ブール値である必要があります。すなわち、true または false。デフォルトでは、demag=false。
  * `H`: 外部フィールド、タプルまたは関数である必要があります。すなわち、[`TupleOrArrayOrFunction`](@ref)。
  * `m0` : 初期磁化、タプルまたは関数である必要があります。すなわち、[`TupleOrArrayOrFunction`](@ref)。
  * `T` : 温度、[`NumberOrArrayOrFunction`](@ref) である必要があります。
  * `shape` : 形状はサンプルの幾何学を定義し、パラメータが設定されます。

```
