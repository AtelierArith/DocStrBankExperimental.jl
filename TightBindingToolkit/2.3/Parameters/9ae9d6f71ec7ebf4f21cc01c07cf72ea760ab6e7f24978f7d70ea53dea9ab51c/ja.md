```julia
GetParams(uc::UnitCell) --> Vector{Param}
```

レガシーの目的のために。古い技術で直接結合を追加して構築された`UnitCell`がある場合、この関数を使用して、`UnitCell`に既に存在する各ユニークな結合タイプに対応する`Param`のベクターを取得できます。
