````
`BdGModel`は、ペアリングを持つ一般的なタイトバインディングシステムを表すデータ型です。

# 属性
- `uc_hop  ::  UnitCell`: ホッピングを持つ格子の単位セル。
- `uc_pair ::  UnitCell`: ペアリングを持つ格子の単位セル。
- `bz      ::  BZ`: 離散化されたブリルアンゾーン。
- `Ham     ::  Hamiltonian`: すべての運動量点でのハミルトニアン。
- `T       ::  Float64`: システムの温度。
- `filling ::  Float64`: システムの充填。
- `mu      ::  Float64`: システムの化学ポテンシャル。
- `stat    ::  Int64` : ボソンとフェルミオンのための±1。
- `gap     ::  Float64` : 与えられた充填での励起のエネルギーギャップ。
- `Gk      ::  Array{Matrix{ComplexF64}}` : `BZ`のk点のグリッドに対応するグリーン関数の配列。
- `Fk      ::  Array{Matrix{ComplexF64}}` : `BZ`のk点のグリッドに対応する異常グリーン関数の配列。

この構造体を初期化するには、次のようにします。
```julia
BdGModel(uc_hop::UnitCell, uc_pair::UnitCell, bz::BZ, Ham::Hamiltonian ; T::Float64=1e-3, filling::Float64=-1.0, mu::Float64=0.0, stat::Int64=-1)
```
充填または化学ポテンシャルのいずれかを入力できます。与えられた充填に対する対応するμ、または与えられたμに対する充填は自動的に計算されます。
````
