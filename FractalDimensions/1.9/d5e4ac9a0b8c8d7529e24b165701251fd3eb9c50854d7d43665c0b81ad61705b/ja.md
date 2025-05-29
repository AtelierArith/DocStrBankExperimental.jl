```
BlockMaxima(blocksize::Int, p::Real)
```

[`extremevaltheory_dims_persistences`](@ref) および関連する関数のための指示タイプ。このメソッドは、入力データを長さ `blocksize` のブロックに分割し、各ブロックの最大値を一般化極値分布にフィットさせます。このメソッドが正しく機能するためには、`blocksize` とブロックの数の両方が高くなければなりません。アルゴリズムによって使用されないデータポイントがあることに注意してください。入力データポイントの数を `N = blocksize * nblocks + 1` と表現することが常に可能であるわけではありません。未使用のデータの数を減らすために、`N` を `blocksize * nblocks + 1` 以上に設定してください。このメソッドとそのいくつかのバリアントは [faranda2011numerical](@cite) で研究されています。

パラメータ `p` は 0 と 1 の間の数で、極値インデックスの計算のための p-分位数を決定します。したがって、[`extremevaltheory_dims_persistences`](@ref) で `compute_persistences = false` の場合は無関係です。

また、[`estimate_gev_parameters`](@ref) も参照してください。
