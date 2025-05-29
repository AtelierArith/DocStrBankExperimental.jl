`Path(isym[,osym], iolabel::Pair, w=one(TropicalWeight{Float32}))`

入力および出力シンボルテーブル `isym` と（オプションの）`osym` を使用してパスを構築します（[`WFST`](@ref]を参照）。

`iolabel` はベクトルの `Pair` です。

```julia
julia> isym = ["a","b","c","d"];

julia> osym = ["α","β","γ","δ"];

julia> W = ProbabilityWeight{Float32};

julia> p = Path(isym,osym,["a","b","c"] => ["α","β","γ"], one(W))
["a", "b", "c"] → ["α", "β", "γ"], w:1.0f0

```

WFST のパスの重みは、通過する異なるアークの重みの乗算 ($\otimes$) から得られます。例えば、[`get_paths`](@ref) を参照して WFST からパスを抽出します。

```julia
julia> p * Path(isym,osym,["d"] => ["δ"], W(0.5))
["a", "b", "c", "d"] → ["α", "β", "γ", "δ"], w:0.5f0

```
