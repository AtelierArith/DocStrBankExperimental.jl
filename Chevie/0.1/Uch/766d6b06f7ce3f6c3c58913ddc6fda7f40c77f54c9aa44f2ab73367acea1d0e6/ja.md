`cuspidal(uc::UnipotentCharacters[,e])`

有限再帰群 `𝐆` のユニポテントキャラクター `γ` は、任意の適切な `e`-分割レヴィへのルスティグ制限がゼロである場合に `e`-カスピダルと呼ばれます。`e==1` の場合（`e` が省略されたときのデフォルト）には、通常のカスピダルキャラクターの概念を回復します。同等に、`γ` の一般的な次数の `Φₑ`-部分は、`𝐆` の随伴群の一般的な次数の `Φₑ`-部分と等しくなります。これは、任意の特別な複素反射群に対して意味があり、それらに対して実装されています。

この関数は、`e`-カスピダルであるユニポテントキャラクターのインデックスのリストを返します。

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> cuspidal(UnipotentCharacters(W))
1-element Vector{Int64}:
 14

julia> cuspidal(UnipotentCharacters(W),6)
8-element Vector{Int64}:
  1
  2
  6
  7
  8
  9
 10
 12

julia> cuspidal(UnipotentCharacters(complex_reflection_group(4)),3)
4-element Vector{Int64}:
  3
  6
  7
 10
```
