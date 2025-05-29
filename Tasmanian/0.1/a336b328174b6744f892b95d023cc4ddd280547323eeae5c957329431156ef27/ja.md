```
makeLocalPolynomialGrid!(tsg::TasmanianSG; order=1, rule="localp", level_limits=Vector{Int32}(undef, 0))
```

は、TSGによって保持されている既存のグリッドを破棄し、ローカル多項式ルールを使用して新しいスパースグリッドを作成します。

order: int (必ず -1 以上である必要があります)         -1 は可能な限り大きな次数を示します          1 は線形、2 は二次、などを意味します          0 は区分定数を意味し、他の次数とは異なる階層を持ちます            特に1Dルールは、他のケースの2倍に対して            各レベルあたりのポイント数を3倍にします。

rule: string (グリッドを誘導する1次元ルールを定義します)       `localp` `localp-zero`  `semi-localp`  `localp-boundary`
