```
MPS(sites::Vector{<:Index},states)
```

サイトインデックス `sites` を持ち、配列 `states` によって与えられる初期状態に対応する積状態 MPS を構築します。`states` 配列は、関連する Index タグタイプのために定義された `state` 関数によって認識される整数または文字列の配列で構成される場合があります。

# 例

```julia
N = 10
sites = siteinds("S=1/2", N)
states = [isodd(n) ? "Up" : "Dn" for n in 1:N]
psi = MPS(sites, states)
```
