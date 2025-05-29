```
Grid(goal=nothing, resolution=10, rng=Random.GLOBAL_RNG, shuffle=true)
```

指定された数のグリッドポイントを `goal` として、または各数値次元で指定されたデフォルトの `resolution` を使用して、Cartesianグリッドベースのハイパーパラメータチューニング戦略をインスタンス化します。

### サポートされている範囲:

単一の1次元範囲または1次元範囲のベクトルを指定できます。具体的には、`Grid` 検索では、`TunedModel` インスタンスの `range` フィールドは次のようにすることができます：

  * 単一の1次元範囲 - すなわち、`ParamRange` オブジェクト - `r`、または形式 `(r, res)` のペアで、ここで `res` はデフォルトの `resolution` を上書きする解像度を指定します。
  * 上記の形式のオブジェクトの任意のベクトル

`range` ベクトルの2つの要素は同じ `field` 属性を共有することができ、その結果、以下の例3のようにグリッドが結合されます。

`ParamRange` オブジェクトは `range` メソッドを使用して構築されます。

例1:

```
range(model, :hyper1, lower=1, origin=2, unit=1)
```

例2:

```
[(range(model, :hyper1, lower=1, upper=10), 15),
  range(model, :hyper2, lower=2, upper=4),
  range(model, :hyper3, values=[:ball, :tree])]
```

例3:

```
# `:hyper1` のためにグリッド `[1, 2, 10, 20, 30]` を生成する範囲:
[range(model, :hyper1, values=[1, 2]),
 (range(model, :hyper1, lower= 10, upper=30), 3)]
```

注意: 前述の例における `ParamRange` オブジェクトのすべての `field` 値（`:hyper1`、`:hyper2`、`:hyper3`）は、単一のモデルのフィールド名（`TunedModel` 構築時に指定された `model`）を参照する必要があります。

### アルゴリズム

これは標準的なグリッド検索で、以下の特定の仕様があります：すべてのケースで、指定された各 `NominalRange` のすべての `values` が消費されます。`goal` が指定されている場合、すべての解像度は無視され、グリッドポイントの数を最大化する `NumericRange` オブジェクトにグローバル解像度が適用されますが、これは `goal` を超えない制限があります。（これは、`range` ベクトルに同じフィールドが2回現れないことを前提としています。）そうでない場合は、デフォルトの `resolution` と任意のパラメータ固有の解像度が適用されます。

すべてのケースで生成されたモデルは、`rng` を使用してシャッフルされます。ただし、`shuffle=false` の場合は除きます。

[`TunedModel`](@ref) や [`range`](@ref) も参照してください。
