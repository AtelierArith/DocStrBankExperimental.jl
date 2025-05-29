```
ASECalculator(; <キーワード引数>)
```

Pythonの[ASE](https://wiki.fysik.dtu.dk/ase)計算機。

この計算機は、PythonCallがインポートされているときのみ利用可能です。必要なPythonパッケージがインストールされていることはユーザーの責任です。これにはASEおよび計算機を提供するパッケージが含まれます。

Mollyの他の部分とは異なり、無次元量はASE単位（長さはÅ、エネルギーはeV、質量はu、時間はÅ sqrt(u/eV)）を持つと仮定されます。有次元量は適切に変換されます。

[`TriclinicBoundary`](@ref)とは現在互換性がありません。

# 引数

  * `ase_calc`: PythonCallで作成されたASE計算機。
  * `atoms`: システム内の原子または原子の同等物。
  * `coords`: システム内の原子の座標。通常は2次元または3次元の`SVector`のベクトルです。
  * `boundary`: シミュレーションが行われるバウンディングボックス。
  * `elements=nothing`: 原子の要素の文字列ベクトル。`elements`または要素データを含む`atoms_data`のいずれかを提供する必要があります。
  * `atoms_data=nothing`: 原子に関連するその他のデータ。
  * `velocities=nothing`: システム内の原子の速度。速度がポテンシャルエネルギーや力に寄与する場合のみ必要です。
