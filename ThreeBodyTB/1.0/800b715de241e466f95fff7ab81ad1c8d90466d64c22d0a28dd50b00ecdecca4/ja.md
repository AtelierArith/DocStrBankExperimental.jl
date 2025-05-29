```
scf_energy_force_stress(c::crystal; database = missing, smearing = 0.01, grid = missing)
```

結晶のエネルギー、力、および応力を計算します。

`return energy, force, stress, tight_binding_crystal_object`

# 引数

  * `c::crystal`: 計算対象の構造。必須の引数。
  * `database=missing`: 係数のソース。欠落している場合は事前にフィットした係数から読み込まれます。
  * `smearing=0.01`: ガウススミアリング温度、単位はリュードベリ。通常はデフォルトのままで問題ありません。
  * `grid=missing`: k点グリッド、例: [10,10,10]、デフォルトは自動的に選択されます。
  * `sparse = :auto`: デフォルトは `nat < 100` の場合に密行列を使用します。選択を強制するために `true` または `false` に設定できます。
