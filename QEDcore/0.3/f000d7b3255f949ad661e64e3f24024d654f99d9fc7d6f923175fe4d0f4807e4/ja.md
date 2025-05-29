```
TwoBodyRestSystem{RESTIDX, COORD<:AbstractUnivariateCoordinate}
```

一方の粒子の静止系における二体散乱系を表し、1つの粒子（`RESTIDX`で識別される）は静止しており、もう1つの粒子の運動量は座標系`COORD`によって記述されます。このシステムは、エネルギー、ラピディティ、または重心エネルギーなど、さまざまな一変数座標を使用して、動いている粒子の運動量をパラメータ化します。

このタイプは、高エネルギー物理プロセスで一般的に使用される二体システムの相空間レイアウトを使用して、入射粒子の運動量を簡単に構築できるようにします。このシステムは、動いている粒子の運動量を定義するための異なる座標系をサポートしており、エネルギーに基づくレイアウトやラピディティに基づくレイアウトが含まれます。

# フィールド

  * `coord::COORD`: 静止していない粒子の運動量を記述するために使用される座標型（`COORD`）。

# サポートされている座標

  * `Energy`: 動いている粒子のエネルギーを定義します。
  * `SpatialMagnitude`: 動いている粒子の空間運動量の大きさを定義します。
  * `CMSEnergy`: システムの全重心エネルギーを定義します。
  * `Rapidity`: 動いている粒子のラピディティを定義します。

# 使用例

以下の例は、`TwoBodyRestSystem`を使用して異なる座標系をどのように使用するかを示しています。

### 例 1: `Energy` 座標を使用

```Julia
psl = TwoBodyRestSystem(Energy(2))  # 粒子1は静止、粒子2はそのエネルギーで記述される
in_coords = (100.0,)  # 粒子2のエネルギー
momenta = build_momenta(proc, model, psl, in_coords)
```

これは、粒子1が静止しており、粒子2が100 GeVのエネルギーを持つと仮定して運動量を構築します。

### 例 2: `SpatialMagnitude` 座標を使用

```Julia
psl = TwoBodyRestSystem(SpatialMagnitude(2))  # 粒子1は静止、粒子2はその空間的な大きさで記述される
in_coords = (50.0,)  # 粒子2の空間運動量の大きさ
momenta = build_momenta(proc, model, psl, in_coords)
```

この場合、動いている粒子の空間運動量の大きさが与えられ、その質量に基づいてエネルギーが計算されます。

### 例 3: `CMSEnergy` 座標を使用

```Julia
psl = TwoBodyRestSystem(1,CMSEnergy())  # 粒子1は静止、粒子2は重心エネルギーで記述される
in_coords = (200.0,)  # システムの全重心エネルギー
momenta = build_momenta(proc, model, psl, in_coords)
```

ここでは、システムの重心エネルギーが提供され、エネルギーと運動量を保存しながら両方の粒子の運動量が計算されます。

### 例 4: `Rapidity` 座標を使用

```Julia
psl = TwoBodyRestSystem(Rapidity(2))  # 粒子1は静止、粒子2はそのラピディティで記述される
in_coords = (1.0,)  # 粒子2のラピディティ
momenta = _build_momenta(proc, model, psl, in_coords)
@assert isapprox(getMass(sum(momenta)),50.0)
```

この場合、粒子2のラピディティが与えられ、そのエネルギーと運動量がこのパラメータに基づいて計算されます。

# 注意事項

  * `RESTIDX`は、システム内で静止している粒子のインデックスです。
  * `COORD`は、静止していない粒子の座標型を指定し、`AbstractUnivariateCoordinate`のサブタイプでなければなりません。
  * 座標系は、与えられた粒子とその質量と互換性がある必要があり、そうでない場合、運動量構築中にエラーが発生する可能性があります。

# 例外

  * 無効な座標が使用された場合（例：サポートされていない座標型や互換性のないインデックス）、`ArgumentError`が発生します。

```
