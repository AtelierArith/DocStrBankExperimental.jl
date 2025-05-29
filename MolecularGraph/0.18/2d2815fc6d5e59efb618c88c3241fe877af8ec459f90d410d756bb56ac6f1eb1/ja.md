```
pi_electron(mol::SimpleMolGraph) -> Vector{Int}
```

与えられた分子の1から$n$番目の原子の$\pi$電子の数を表すサイズ$n$のベクトルを返します。

$$
\pi
$$

電子の数は`valence` - `connectivity`として計算されます。通常、二重結合に接続された各原子はそれぞれ1つの$\pi$電子を追加し、三重結合に接続された各原子は2つの$\pi$電子を追加します。
