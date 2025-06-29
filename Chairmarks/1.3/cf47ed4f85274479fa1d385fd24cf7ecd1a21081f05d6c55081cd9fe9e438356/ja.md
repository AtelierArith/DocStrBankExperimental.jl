```
struct Sample
    evals              ::Float64 # このサンプルのベンチマークが評価された回数。
    time               ::Float64 # サンプルを実行するのにかかった平均時間（評価ごとの秒数）。
    allocs             ::Float64 # 評価ごとに行われた平均アロケーション数
    bytes              ::Float64 # 評価ごとにアロケートされた平均バイト数
    gc_fraction        ::Float64 # ガーベジコレクションに費やされた時間の割合（0.0から1.0）
    compile_fraction   ::Float64 # コンパイルに費やされた時間の割合（0.0から1.0）
    recompile_fraction ::Float64 # コンパイル時間のうち、再コンパイルであった割合（0.0から1.0）
    warmup             ::Float64 # このサンプルが実行される前にウォームアップがあったかどうか（1.0 = はい。0.0 = いいえ）。
    ...more fields may be added...
end
```

ベンチマークの単一サンプルを表す構造体。

[`@b`](@ref) は、測定されたサンプルのフィールドごとの最小値を取ることによって形成された合成サンプルを返します。将来的には、より多くの情報が得られるにつれて、さらにフィールドが追加される可能性があります。
