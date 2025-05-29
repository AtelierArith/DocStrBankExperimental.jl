```
Δnout!([utilityfun], v, Δ...)
Δnout!([utilityfun], v1 => Δ1, v2 => Δ2,...)
Δnout!([utilityfun], Δs::AbstractDict)

提供されたすべての頂点の出力サイズを関連する `Δ` で変更し、グラフが活性化に関して整列するように他の頂点に適切な変更を加えます。成功した場合は `true` を返し（成功しなかった場合は `false` を返します）。

整数として提供された `Δ` の場合、サイズを正確に `Δ` だけ変更することが可能でなければ、試みは失敗と見なされます。失敗した試みは、望ましいサイズ変更が目的に移動される緩和された形で即座に再試行されます。緩和とは、出力サイズが正確に `Δ` だけ変更されない可能性があることを意味します。初回の試みでサイズ変更が緩和されていることを示すには [`relaxed(Δ)`](@ref) を使用します。

引数 `utilityfun` は、同じグラフ内の任意の頂点 `vx` に対してベクトル `utility = utilityfun(vx)` を提供します。ここで `utility[i] > utility[j]` は、頂点 `vx` に対して出力ニューロンインデックス `i` が `j` よりも優先されるべきであることを示します。また、スカラーを提供することもでき、これは `vx` のすべてのニューロンの効用として使用されます。提供されない場合は、[`defaultutility(vx)`](@ref) が使用されます。

`Δnout!([utilityfun], args...)` は `Δsize!([utilityfun], ΔNout(args...))` と同等です。

### 例

```

jldoctest julia> using NaiveNASlib, NaiveNASlib.Extend, NaiveNASlib.Advanced

julia> module TestNNLib            using NaiveNASlib, NaiveNASlib.Extend            mutable struct Affine{T} W::Matrix{T} end            NaiveNASlib.nout(a::Affine) = size(a.W, 1)            NaiveNASlib.nin(a::Affine) = [size(a.W, 2)]            NaiveNASlib.Δsize!(a::Affine, ins::AbstractVector, outs::AbstractVector) = a.W = parselect(a.W, 2=>ins[1], 1=>outs)            affine(in, outsize) = absorbvertex(Affine(ones(outsize, nout(in))), in)            export affine        end;

julia> using .TestNNLib;

julia> iv = affine(inputvertex("in", 3), 6);

julia> v1 = affine(iv, 4);

julia> v2 = affine(iv, 5);

julia> Δnout!(v1, 3);

julia> Δnout!(v1 => -3, v2 => -2);

julia> Δnout!(Dict(v1 => 3, v2 => 2));

julia> Δnout!(v1, relaxed(2));

julia> Δnout!(v1 => relaxed(2), v2 => -1) do v            randn(nout(v))        end; ```
