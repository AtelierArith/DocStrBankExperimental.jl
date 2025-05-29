```
anim_transition!(canvas, renderer, domain, state, [action, t];
                 callback=nothing, overlay=nothing, kwargs...)
```

現在の状態を `canvas` に保存された状態から新しく提供された `state` へ（提供された場合は `action` による時刻 `t` で）遷移させるアニメーションを行います。これは [`anim_plan`](@ref) および [`anim_trajectory`](@ref) によって一連の状態遷移をアニメーション化するために呼び出されます。

デフォルトでは、これにより `canvas` が新しい `state` で更新され、その後 `overlay` および `callback` 関数（提供されている場合）が `canvas` 上で実行されます（例：注釈を重ねたり、フレームを記録したりするため）。

この関数は、カスタム遷移を実装するために異なる [`Renderer`](@ref) タイプに対してオーバーロードすることができます。例えば、複数のフレームを含む遷移などです。
