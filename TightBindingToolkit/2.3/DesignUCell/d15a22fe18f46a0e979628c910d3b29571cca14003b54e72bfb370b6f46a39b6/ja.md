```julia
Lookup(uc::UnitCell) --> Dict
```

`UnitCell`のボンドリストに対して、キーが(base, target, offset)である辞書を返し、エントリはボンド行列です。同じ識別子を持つボンドが複数ある場合、それらを合計します。
