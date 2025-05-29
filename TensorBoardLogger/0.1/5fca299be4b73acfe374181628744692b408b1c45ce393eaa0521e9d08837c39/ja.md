`with_TBLogger_hold_step(f, [step]; step_at_end::Bool=true)` ロギングステップと同期の制御を容易にするコンテキスト関数。ステップの増分の量は `set_step_increment!` を介して制御できます。

例:

```julia
with_logger(lg) do
    for epoch in 1:10
        for i=1:100
            # デフォルトでglobal_stepを増加させる
            with_TBLogger_hold_step() do
                # これらはすべて同じglobal_stepでログされる
                # そしてロガーのglobal_stepはその時にのみ増加する
                @info "train1/scalar" i=i
                @info "train2/scalar" i2=i^2
                @info "train3/scalar" i3=i^3
            end
        end
        # 簡単なtrain/test同期のために、終了時のステップ増加を無効にすることができる
        with_TBLogger_hold_step(;step_at_end=false) do
            # これらはすべて同じglobal_stepでログされる
            # そしてロガーのglobal_stepはその時にのみ増加する
            @info "test1/scalar" i=i
            @info "test2/scalar" i2=i^2
            @info "test3/scalar" i3=i^3
        end
    end
end
```
