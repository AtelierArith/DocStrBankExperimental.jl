```
findsite(M::Union{MPS, MPO}, is)
```

MPSまたはMPOの最初のサイトを返します。これは、インデックスまたはインデックスのコレクション`is`と少なくとも1つのインデックスが共通しているサイトです。

`is`と共通のインデックスを持つすべてのサイトを見つけるには、`findsites`関数を使用してください。

# 例

```julia
s = siteinds("S=1/2", 5)
ψ = random_mps(s)
findsite(ψ, s[3]) == 3
findsite(ψ, (s[3], s[4])) == 3

M = MPO(s)
findsite(M, s[4]) == 4
findsite(M, s[4]') == 4
findsite(M, (s[4]', s[4])) == 4
findsite(M, (s[4]', s[3])) == 3
```
