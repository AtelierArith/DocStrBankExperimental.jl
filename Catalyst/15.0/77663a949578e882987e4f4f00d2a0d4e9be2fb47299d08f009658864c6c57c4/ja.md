```
complexoutgoingmat(network::ReactionSystem; sparse=false)
```

与えられた [`ReactionSystem`](@ref) と複雑な入出力行列 $B$ に対して、基質複合体を特定する複雑出力行列のサイズが複合体の数と反応の数の行列を返します。

注意:

  * 複雑出力行列 $\Delta$ は次のように定義されます。

$$
\Delta_{i j} = \begin{cases}
    = 0,    &\text{if } B_{i j} = 1, \\
    = B_{i j}, &\text{otherwise.}
\end{cases}
$$

  * スパース行列表現のために sparse=true を設定します。
