`collectpaths(fst::FST, [i = get_initial(fst;first=true)])`

`fst`のすべての可能なパスを、`i`から始めて含む配列を返します。

アルゴリズムが停止するためには、`fst`が非循環である必要があることに注意してください（[`is_acyclic`](@ref)を参照）。
