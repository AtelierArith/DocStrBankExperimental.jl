```
TrivialAtomBijection{T} <: AbstractAtomBijection{T}
```

関連する原子コンテナ内の順序に基づく原子の双射。

# コンストラクタ

```julia
TrivialAtomBijection(A::AtomTable{T}, B::AtomTable{T})
```

与えられたテーブルから新しい `TrivialAtomBijection{T}` を作成します。原子の順序は行番号によって決まります。

```julia
TrivialAtomBijection(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
```

個々の原子コンテナの原子を使用して新しい `TrivialAtomBijection{T}` を作成します。

```julia
TrivialAtomBijection(A::AtomTable{T}, B::AbstractAtomContainer{T})
```

`A` に含まれる原子番号のために `B` をフィルタリングすることによって新しい `TrivialAtomBijection{T}` を作成します。フィルタリング後の原子の順序は `A` と同じでなければなりません。
