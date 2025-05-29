```
outer(x::MPS, y::MPS; <keyword argument>) -> MPO
```

`MPS` `x` と `MPS` `y` の外積を計算し、`MPO` 近似を返します。`y` は共役になります。

ディラック記法では、この操作は `|x⟩⟨y|` です。

MPS の外積を自身と計算したい場合は、`outer(x', x; kwargs...)` を呼び出す必要があります。そうすることで、結果の MPO はプライムレベルの 1 と 0 のペアでインデックスが入るサイトインデックスを持ちます。そうでない場合、サイトインデックスは一意ではなくなり、外積にはなりません。

例えば：

```julia
s = siteinds("S=1/2", 5)
x = random_mps(s)
y = random_mps(s)
outer(x, y) # 不正！サイトインデックスは一意でなければなりません。
outer(x', y) # プライムインデックスと非プライムインデックスのペアを持つ MPO が得られます。
```

これにより、プライムインデックスと非プライムインデックスのペアを持たないより一般的な外積や、入力 MPS が MPO のベクトル化である外積が可能になります。

例えば：

```julia
s = siteinds("S=1/2", 5)
X = MPO(s, "Id")
Y = MPO(s, "Id")
x = convert(MPS, X)
y = convert(MPS, Y)
outer(x, y) # 不正！サイトインデックスは一意でなければなりません。
outer(x', y) # 不正！サイトインデックスは一意でなければなりません。
outer(addtags(x, "Out"), addtags(y, "In")) # これが適切な外積を実行します。
```

キーワード引数は切り捨てを決定し、`contract(::MPO, ::MPO; kwargs...)` と同じ引数を受け入れます。

[`apply`](@ref) や [`contract`](@ref) も参照してください。
