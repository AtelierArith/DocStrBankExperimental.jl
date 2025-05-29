@protostruct(struct_ [, prefix_])

構造体を作成し、それから構造を継承でき、構造を継承することができます。

さらに、構造体定義の名前とプレフィックスによって与えられた名前の抽象型を作成します。具体的な型は抽象型から継承し、具体的な型の構造を継承するものはすべて抽象型からの動作も継承します。

```Julia
julia> using StructuralInheritance

julia> @protostruct struct A{T}
           fieldFromA::T
       end
ProtoA

julia> @protostruct struct B{D} <: A{Complex{D}}
          fieldFromB::D
       end "SomeOtherPrefix"
SomeOtherPrefixB

julia> @protostruct struct C <: B{Int}
         fieldFromC
       end
ProtoC
```
