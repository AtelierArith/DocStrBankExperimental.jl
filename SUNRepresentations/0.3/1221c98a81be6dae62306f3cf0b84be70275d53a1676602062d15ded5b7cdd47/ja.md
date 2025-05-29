```
struct SUNIrrep{N} <: AbstractIrrep{SU{N}}
```

最高重み `I` を持つ SU(N) の表現。

# コンストラクタ

```
SUNIrrep(I::NTuple{N,Int})
SUNIrrep(args::Vararg{Int})
```

最高重み `I` または `args...` を持つ `SU{N}` の表現を構築します。

```
SUNIrrep{N}(name::AbstractString)
```

次元名 `name` を持つ `SU{N}` の表現を構築します。パラメータ `N` は表現を一意に識別するために必要です。

```
SUNIrrep(a::Vector{Int})
```

最高重み `a = [a₁, a₂, …, aₙ₋₁]` を持つ `SU{N}` の表現を構築します。
