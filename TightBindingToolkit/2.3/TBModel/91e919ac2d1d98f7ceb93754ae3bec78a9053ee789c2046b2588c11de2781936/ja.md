`Model`は一般的なタイトバインディングシステムを表すデータ型です。

# 属性

  * `uc      ::  UnitCell`: 格子の単位セル。
  * `bz      ::  BZ`: 離散化されたブリルアンゾーン。
  * `Ham     ::  Hamiltonian`: すべての運動量点でのハミルトニアン。
  * `T       ::  Float64`: システムの温度。
  * `filling ::  Float64`: システムの充填。
  * `mu      ::  Float64`: システムの化学ポテンシャル。
  * `stat    ::  Int64` : ボソンとフェルミオンのための±1。
  * `gap     ::  Float64` : 与えられた充填での励起のエネルギーギャップ。
  * `Gk      ::  Array{Matrix{ComplexF64}}` : `BZ`のk点のグリッドに対応するグリーン関数の配列。

この構造体は次のように初期化します。

```julia
Model(uc::UnitCell, bz::BZ, Ham::Hamiltonian ; T::Float64=1e-3, filling::Float64=-1.0, mu::Float64=0.0, stat::Int64=-1)
```

充填または化学ポテンシャルのいずれかを入力できます。与えられた充填に対する対応するμ、または与えられたμに対する充填は自動的に計算されます。
