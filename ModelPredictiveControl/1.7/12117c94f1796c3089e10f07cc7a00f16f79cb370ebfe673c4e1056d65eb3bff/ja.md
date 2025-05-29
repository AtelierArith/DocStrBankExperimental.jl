```
periodsleep(model::SimModel, busywait=false) -> nothing
```

`model.Ts` 秒から最後の[`savetime!`](@ref)の呼び出しから経過した時間を引いた時間だけスリープします。

`busywait`が`false`の場合は[`sleep`](@extref Julia Base.sleep)を呼び出します。それ以外の場合は、単純な`while`ループでビジーウェイトを実装します。一般的な目安として、`model.Ts < 0.1`秒の場合はビジーウェイトを使用すべきです。なぜなら、`sleep`の精度は約1ミリ秒だからです。以下の例のように、単純なソフトリアルタイムシミュレーションを実装するために使用できます。

!!! warning
    Juliaのアロケーションは自動的にガーベジコレクション（GC）されます。これがタイミングに影響を与える可能性があります。そのような場合は、`GC.enable(false)`で一時的にGCを停止し、`periodsleep`を呼び出す直前など、都合の良いタイミングで再起動できます。


# 例

```jldoctest
julia> model = LinModel(tf(2, [0.3, 1]), 0.25);

julia> function sim_realtime!(model)
           t_0 = time()
           for i=1:3
               t = savetime!(model)      # 最初に呼び出される関数
               println(round(t - t_0, digits=3))
               updatestate!(model, [1])
               periodsleep(model, true)  # 最後に呼び出される関数
           end
       end;

julia> sim_realtime!(model)
0.0
0.25
0.5
```
