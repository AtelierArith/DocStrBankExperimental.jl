ベル保存ゲートは、単一のベルペアに対して4つの可能な「パウリ置換」の1つを実行します。

これは、ベルペアのアリス側にパウリゲートを適用するのと同等です。

最初の引数 `pidx` は置換を指定します（1から4の間）。2番目の引数 `sidx` は、作用するベルペアを示します。

```jldoctest
julia> BellPauliPermutation(1,1)*BellState(1) |> Stabilizer
+ XX
+ ZZ

julia> BellPauliPermutation(2,1)*BellState(1) |> Stabilizer
+ XX
- ZZ

julia> BellPauliPermutation(3,1)*BellState(1) |> Stabilizer
- XX
+ ZZ

julia> BellPauliPermutation(4,1)*BellState(1) |> Stabilizer
- XX
- ZZ
```
