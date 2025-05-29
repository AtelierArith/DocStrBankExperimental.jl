```
 ExpectationValue(G::Matrix{F},
      si::Vector{Int64},
      dagidx::Vector{Int64}) -> ::F
```

複数のフェルミオン演算子の期待値を返します。`si`はサイトを示し、`dagidx`は演算子がダガーかどうかを示します。例えば、`si = [i, j]`および`dagidx = [2]`は単一粒子相関`c_i c_j^dag`を意味し、`si = [i, j, k, l]`および`dagidx = [3, 4]`はペアリング相関`c_i c_j c_k^dag c_l^dag`を意味します。
