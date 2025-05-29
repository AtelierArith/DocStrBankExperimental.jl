```
findsites(M::Union{MPS, MPO}, is)
```

MPSまたはMPOのサイトを返します。これらのサイトは、サイトインデックスのコレクション`is`と共通のインデックスを持っています。

# 例

```julia
s = siteinds("S=1/2", 5)
ψ = random_mps(s)
findsites(ψ, s[3]) == [3]
findsites(ψ, (s[4], s[1])) == [1, 4]

M = MPO(s)
findsites(M, s[4]) == [4]
findsites(M, s[4]') == [4]
findsites(M, (s[4]', s[4])) == [4]
findsites(M, (s[4]', s[3])) == [3, 4]
```
