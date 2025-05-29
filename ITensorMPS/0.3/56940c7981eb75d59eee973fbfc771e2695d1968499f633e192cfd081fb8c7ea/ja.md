```
MPS(::Type{T},
    sites::Vector{<:Index},
    states::Union{Vector{String},
                  Vector{Int},
                  String,
                  Int})
```

要素型 `T` の積状態 MPS を構築し、サイトインデックス `sites` を持ち、配列 `states` によって与えられる初期状態に対応します。入力 `states` は、関連する Index タグ型のために定義された `state` 関数によって認識される文字列の配列または整数の配列である可能性があります。さらに、単一の文字列または整数を入力して均一な状態を作成することもできます。

# 例

```julia
N = 10
sites = siteinds("S=1/2", N)
states = [isodd(n) ? "Up" : "Dn" for n in 1:N]
psi = MPS(ComplexF64, sites, states)
phi = MPS(sites, "Up")
```
