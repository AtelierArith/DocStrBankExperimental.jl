```
ghash(g::AbstractNautyGraph)
```

`g`の標準形のハッシュを計算します。したがって（ハッシュの衝突を除いて）`ghash(g1) == ghash(g2)`が成り立つ場合、`is_isomorphic(g1, g2) == true`が成り立ちます。ハッシュは、小さなグラフ（nv < 8192）の場合は`Base.hash`を使用して計算され、より大きなグラフの場合は`sha256`の最初の64ビットを使用して計算されます。
