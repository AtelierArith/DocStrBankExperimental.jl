```julia
generateGraph_Boxes2D!(; ...)
generateGraph_Boxes2D!(
    numposes;
    graphinit,
    dfg,
    useMsgLikelihoods,
    length_x,
    length_y,
    slew_x,
    poseRegex,
    refKey,
    Qd,
    postpose_cb
)

```

x軸とy軸に沿ったボックス形状のための標準的なグラフ生成器で、デフォルトの動作は各新しいボックスをx軸に沿って2/3のオーバーラップでスルーさせます。

ノート

  * 関数はまだ実験的です
  * TODO 現在`numposes`は新しいボックスの各コーナーに対して4の倍数で動作します – すなわち8 –> 2ボックス。
  * 各ポーズ変数がグラフに追加された後の追加の動作には`postpose_cb(fg, lastpose)`を使用してください。

関連

[`generateGraph_ZeroPose`](@ref), [`generateGraph_Helix2DSlew!`](@ref), [`generateGraph_Hexagonal`](@ref)
