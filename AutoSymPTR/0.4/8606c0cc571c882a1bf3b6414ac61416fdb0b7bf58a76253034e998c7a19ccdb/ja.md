```
autosymptr(f, B::AbstractMatrix, [syms=nothing]; atol=0, rtol=sqrt(eps()), maxevals=typemax(Int64), buffer=nothing)
```

指定された許容範囲内で `f` の積分を計算し、推定された積分、推定誤差、積分評価の数を含むタプル `(I, E, numevals, rules)` を返します。対称化された領域での積分は、対称性の作用の下での被積分関数の表現に依存するため、呼び出し元によって元の領域にマッピングされる必要があります。

被積分関数の評価を格納するためにベクターバッファが提供される場合、被積分関数の評価は並列化され、被積分関数がスレッドセーフであると仮定されます。

!!! note "収束は周期性に依存します"
    ルーチンが長時間返さない場合は、`B` の列の基底ベクトルに沿った関数 `f` の周期が一貫しているか再確認してください。

