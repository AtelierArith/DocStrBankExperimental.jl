```julia
generateGraph_Helix2DSpiral!(; ...)
generateGraph_Helix2DSpiral!(
    numposes;
    rate_r,
    rate_a,
    spine_t,
    kwargs...
)

```

スパイラルパターンに沿って拡張する標準的なヘリックスグラフを生成します。花びらに類似しています。

ノート

  * この関数は、スパイラルパターンを生成するために複雑な `spine_t(t)` 関数をラップします。

      * `rate_a` と `rate_r` は、異なるスパイラルの挙動のために変化させることができます。
  * より詳細な情報については、一般化されたヘリックスジェネレーターを参照してください。
  * デフォルトは、ヘリックスの連続ループ間で複数の軌道交差を持つように選択され、相対的な囲まれた面積のサイズのバランスを保ちながらカバレッジエリアを移動するのに適した仕事をします。

関連 

[`generateGraph_Helix2D!`](@ref), [`generateGraph_Helix2DSlew!`](@ref)
