`QuantumElectrodynamics.jl`の文脈で*粒子*と見なされる可能性のあるすべての型のための抽象基本型。`AbstractParticle`のすべての（具体的な）サブタイプには、静的関数とプロパティ関数の2種類のインターフェース関数が実装されています。静的関数は、それがどのような粒子であるかに関する情報を提供します（デフォルトは角括弧内に書かれています）。

```julia
    is_fermion(::AbstractParticle)::Bool [= false]
    is_boson(::AbstractParticle)::Bool [= false]
    is_particle(::AbstractParticle)::Bool [= true]
    is_anti_particle(::AbstractParticle)::Bool [= false]
```

これらの関数の出力が`AbstractParticle`のサブタイプのデフォルトと異なる場合、これらの関数は上書きする必要があります。2番目のタイプの関数は、`AbstractParticle`のためのハードインターフェースを定義します：

```julia
    mass(::AbstractParticle)::Real
    charge(::AbstractParticle)::Real
```

これらの関数は、`AbstractParticle`のサブタイプが`QEDprocesses.jl`の機能と連携するために実装されなければなりません。
