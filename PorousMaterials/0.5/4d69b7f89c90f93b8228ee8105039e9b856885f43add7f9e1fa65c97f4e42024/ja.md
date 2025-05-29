```
molecule = Molecule(species, check_neutrality=true)
```

入力ファイルから `joinpath(rc[:paths][:molecules], species)` を読み込んで `Molecule` を構築します。

重心は `rc[:atomic_masses]` からの原子量を使用して割り当てられます。

# 引数

  * `species::String`: 分子の名前
  * `check_neutrality::Bool`: 安全のために分子が電荷中性であることを確認します。

# 戻り値

  * `molecule::Molecule{Cart}`: カルテシアン座標の分子
