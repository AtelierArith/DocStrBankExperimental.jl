```julia
update_cache!(cache, H, p, t)

```

与えられた時間 `t` におけるハミルトニアン `H` の値に従って内部キャッシュ `cache` を更新します: $cache = -iH(p, t)$。第三引数 `p` は、`AbstractHamiltonian` オブジェクトに追加情報を渡すために予約されています。現在のところ、これは `AdiabaticFrameHamiltonian` によって、総進化時間 `tf` を渡すためにのみ使用されています。すべての `AbstractHamiltonian` タイプでインターフェースを一貫させるために、すべての `AbstractHamiltonian` のサブタイプに対する `update_cache!` メソッドは引数 `p` を保持する必要があります。

一般的な `AbstractHamiltonian` タイプの場合は、`cache .= -1.0im * H(p, t)` にフォールバックします。
