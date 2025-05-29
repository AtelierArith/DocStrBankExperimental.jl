```
anim_refine!([path], renderer,
             sol, planner, domain, state, spec;
             format="mp4", framerate=30, show=false,
             record_init=true, copy_sol=false, options...)

anim_refine!([anim|path], canvas, renderer,
             sol, planner, domain, state, spec;
             format="mp4", framerate=30, show=is_displayed(canvas),
             record_init=true, copy_sol=false, options...)
```

`renderer`を使用して、PDDL `domain`内のSymbolicPlanners.jl `planner`による既存の解の洗練をアニメーション化します（提供された場合は`canvas`を更新します）。

タプル`(anim, sol)`を返します。ここで、`anim`はアニメーションを含む[`Animation`](@ref)オブジェクトであり、`sol`は`planner`によって返された解です。最初の引数として`anim`が提供されている場合、追加のフレームがアニメーションに追加されます。あるいは、`path`が提供されている場合、アニメーションはそのファイルに保存され、`(path, sol)`が返されます。`copy_sol`が`true`の場合、洗練の前に初期解のコピーが作成されます。

アニメーションが表示または保存されると、フレームを追加することはできないことに注意してください。
