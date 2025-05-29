```
function set_units(;energy=missing, length=missing, both=missing)
```

エネルギー/長さのグローバル単位を設定します。引数なしで実行すると、現在の単位を確認/返します。

  * デフォルトの単位は `"eV"` と `"Angstrom"` （または `"Å"` または `"Ang"` ）です。
  * `energy="Ryd"` と `length="Bohr"` を設定することで原子単位を選択します。
  * `both="atomic"` または `both="eVAng"` を使用して両方を同時に設定します。
  * 内部的には、すべての単位は原子単位です。実際に単位を変更するのは、主に公開されている関数のみです。
