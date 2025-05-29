```
Δnin!([utilityfun], v, Δ...)
Δnin!([utilityfun], v1 => Δ1, v2 => Δ2,...)
Δnin!([utilityfun], Δs::AbstractDict)

提供されたすべての頂点の入力サイズを関連する `Δ` で変更し、グラフがアクティベーションに関して整列するように他の頂点に適切な変更を加えます。成功した場合は `true` を返し（成功しなかった場合は `false` を返します）。

整数として提供された `Δ` に対しては、サイズを正確に `Δ` だけ変更することが可能でなければ、試みは失敗と見なされます。失敗した試みは、望ましいサイズ変更が目的に移動される緩和された形で即座に再試行されます。緩和とは、入力サイズが正確に `Δ` だけ変更されない可能性があることを意味します。初回の試みでサイズ変更が緩和されていることを示すために [`relaxed(Δ)`](@ref) を使用します。

複数の入力を持つ頂点に対しては、サイズ変更は各入力ごとに1つの要素を持つタプルとして表現する必要があります。特別な処理が必要ない入力を示すために `missing` を使用します。`missing` と [`relaxed`](@ref) は、タプルの内外で自由に混ぜることができます（例を参照）。

上記の制約により、`Δnin!` は [`Δnout!`](@ref) と比較して使用がはるかに面倒になります。ほとんどの場合、`Δnin!` を使用する直接的な利点はなく、両者は同じことに帰着します。

引数 `utilityfun` は、同じグラフ内の任意の頂点 `vx` に対してベクトル `utility = utilityfun(vx)` を提供します。ここで `utility[i] > utility[j]` は、出力ニューロンインデックス `i` が頂点 `vx` に対して `j` よりも優先されるべきであることを示します。また、`vx` のすべてのニューロンのユーティリティとして使用されるスカラーを提供することもできます。提供されない場合は、[`defaultutility(vx)`](@ref) が使用されます。

`Δnin!([utilityfun], args...)` は `Δsize!([utilityfun], ΔNin(args...))` と同等です。

### 例

```

jldoctest julia> using NaiveNASlib, NaiveNASlib.Extend, NaiveNASlib.Advanced

julia> module TestNNLib            using NaiveNASlib, NaiveNASlib.Extend            mutable struct Affine{T} W::Matrix{T} end            NaiveNASlib.nout(a::Affine) = size(a.W, 1)            NaiveNASlib.nin(a::Affine) = [size(a.W, 2)]            NaiveNASlib.Δsize!(a::Affine, ins::AbstractVector, outs::AbstractVector) = a.W = parselect(a.W, 2=>ins[1], 1=>outs)            affine(in, outsize) = absorbvertex(Affine(ones(outsize, nout(in))), in)            export affine        end;

julia> using .TestNNLib;

julia> iv = affine(inputvertex("in", 3), 6);

julia> v1 = affine(iv, 4);

julia> v2 = affine(iv, 5);

julia> Δnin!(v1, 3);

julia> Δnin!(v1 => -3, v2 => -2);

julia> Δnin!(Dict(v1 => 3, v2 => 2));

julia> v3 = conc(affine(iv, 4), affine(iv, 5), affine(iv, 6); dims=2);

julia> v4 = conc(affine(iv, 7), affine(iv, 8); dims=2);

julia> Δnin!(v3, 3, missing, 2);

julia> Δnin!(v3 => (3, missing, 2), v4 => (-2, 0));

julia> Δnin!(v3, relaxed(3), missing, 2);

julia> Δnin!(v3 => (relaxed(3), missing, 2), v4 => relaxed(-2, 0)) do v            randn(nout(v))        end; ```
