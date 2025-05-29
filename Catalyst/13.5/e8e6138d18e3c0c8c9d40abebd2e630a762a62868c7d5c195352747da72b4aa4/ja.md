```
complexstoichmat(network::ReactionSystem; sparse=false)
```

与えられた [`ReactionSystem`](@ref) と反応複合体のベクトルに対して、種の数と複合体の数のサイズを持つ正のエントリの行列を返します。k番目の列の非ゼロの正のエントリは、k番目の反応複合体に参加する種のストイキオメトリック係数を示します。

注意:

  * スパース行列表現のために sparse=true を設定してください。
