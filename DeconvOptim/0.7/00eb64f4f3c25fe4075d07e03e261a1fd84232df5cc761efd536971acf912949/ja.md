```
plan_conv(u, v [, dims])
```

`u` と `v` の形状に基づいて最適化された畳み込みを事前に計画します（事前計画 FFT に基づく）。デフォルトでは `dims = 1:ndims(u)` です。`u` の 0 周波数は最初のエントリに配置されている必要があります。2 つの引数を返します。最初の引数は `v_ft`（`fft(v)` または `rfft(v)` によって得られます）。2 番目の返り値は畳み込み関数 `pconv` です。`pconv` 自体は 2 つの引数を持ちます。`pconv(u, v_ft=v_ft)` で、`u` はオブジェクトで、`v_ft` は v_ft です。この関数は `conv(u, u)` よりも高速な畳み込みを実現します。`u` が実数か複素数かに応じて、`fft` または `rfft` を行います。

# 警告

`pconv` 関数の結果出力は、内部で割り当てられた配列への参照です。異なるタスクに `pconv` 関数を使用すると、新しい `pconv` の呼び出しが以前の結果を変更します（以前の結果は新しい配列ではなく、参照のみだったためです）。

# 例

```jldoctest
julia> u = [1 2 3 4 5]
1×5 Matrix{Int64}:
 1  2  3  4  5
julia> v = [1 0 0 0 0]
1×5 Matrix{Int64}:
 1  0  0  0  0
julia> v_ft, pconv = plan_conv(u, v);
julia> pconv(u, v_ft)
1×5 Matrix{Float64}:
 1.0  2.0  3.0  4.0  5.0
julia> pconv(u)
1×5 Matrix{Float64}:
 1.0  2.0  3.0  4.0  5.0
```
