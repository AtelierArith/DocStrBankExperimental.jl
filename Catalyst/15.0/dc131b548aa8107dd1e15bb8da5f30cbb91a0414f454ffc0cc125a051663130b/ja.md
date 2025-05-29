```
reactioncomplexes(network::ReactionSystem; sparse=false)
```

与えられた [`ReactionSystem`](@ref) の反応複合体と複合体発生行列を計算します。

注意事項：

  * [`ReactionComplex`](@ref) のベクトルと複合体発生行列のペアを返します。
  * 空の [`ReactionComplex`](@ref) は null (∅) 状態を示します（∅ -> A または A -> ∅ のような反応から）。
  * 定数種は反応複合体の生成に無視されます。すなわち、A が定数である場合、A –> B は複合体 ∅ と B から成ります。
  * 複合体発生行列 $B$ は、複合体の数と反応の数で構成され、次のようになります。

$$
B_{i j} = \begin{cases}
-1, &\text{もし i 番目の複合体が j 番目の反応の基質である場合},\\
1, &\text{もし i 番目の複合体が j 番目の反応の生成物である場合},\\
0, &\text{それ以外の場合.}
\end{cases}
$$

  * 発生行列の疎行列表現のために sparse=true を設定します。
