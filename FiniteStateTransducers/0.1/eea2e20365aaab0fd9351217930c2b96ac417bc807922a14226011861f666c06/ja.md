`get_paths(fst::FST, [i = get_initial(fst;single=true)])`

`fst`のすべての可能なパスを生成するイテレータを返します。`i`から始まります。

アルゴリズムが停止するためには、`fst`が非循環である必要があります（[`is_acyclic`](@ref）を参照）。
