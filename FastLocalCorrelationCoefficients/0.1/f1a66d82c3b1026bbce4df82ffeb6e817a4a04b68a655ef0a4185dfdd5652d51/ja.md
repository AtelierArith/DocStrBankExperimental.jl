```
  flcc(haystack,needle)
```

局所的（ピアソン）相関係数を計算します。

$$
\mathrm{lcc}(x,y) = \frac{(x - \mu_x)^T(y - \mu_y)}{\sigma_x \sigma_y}
$$

`needle` と `haystack` 内の同じサイズのすべてのスライディングウィンドウとの間の相関を計算します。

`flcc` は、高速フーリエ変換を使用して計算の複雑さを O($n_H n_N$) から O(($n_H + n_N) \log(n_H + n_N)$) に削減します。ここで、$n_H$ と $n_N$ はそれぞれ `haystack` と `needle` の要素数です。

`flcc` は、実数または複素数のエントリを持つ任意の次元のテンソルをサポートします。

# 例

`haystack` が実数のテンソルで、`needle` が同じ次元の小さなテンソルであるとします。`haystack` 内で `needle` を探そうとしています。`needle` はスケーリングおよび平行移動されている可能性があることに注意してください。

`LCC` の最大要素の位置は、`needle` と `haystack` のスライディングウィンドウとの間の最適な一致です。

```jldoctest
julia> using FastLocalCorrelationCoefficients

julia> haystack = rand(2^10,2^10);

julia> needle = rand(1) .* haystack[42:48, 45:50] .+ rand(1);

julia> c = flcc(haystack,needle);

julia> best_correlated(c)
CartesianIndex(42, 45)
```

同じサイズの多くの `needle` を検索する必要がある場合、

```
  haystack = rand(2^20);
  needle1 = rand(1) .* haystack[2:8] .+ rand(1);
  needle2 = rand(1) .* haystack[42:48] .+ rand(1);
  needle3 = rand(1) .* haystack[end-6:end] .+ rand(1);
```

`haystack` を前処理して、すべての共通情報を事前に計算することで冗長な計算を避けることができます。直接法を使用する場合にはそのような前処理はありません。

```
  precomp = flcc(haystack,size(needle1));

```

その後、はるかに高速なクエリのためにそれを使用します。

```
  best_correlated(flcc(precomp,needle1)) == 2
  best_correlated(flcc(precomp,needle2)) == 42
  best_correlated(flcc(precomp,needle3)) == 2^20-6
```
