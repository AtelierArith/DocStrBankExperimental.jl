```julia
VortexFilament(Γ, v; ...)
VortexFilament(Γ, v, boundidx; isclosed)

```

`Γ`の強さと頂点`v`を持つ`VortexFilament`を構築します。`boundidx`は「バウンド」と見なされる頂点のインデックスを提供するために使用できます。コンストラクタは、`VortexFilament`の`freeidx`をインデックスの補完リストとして設定します。キーワード`isclosed`が`true`の場合、`VortexFilament`の`segments`には、`v`の最初と最後の頂点を接続するセグメントが含まれます。ただし、これらが無限の座標を含まない場合に限ります。
