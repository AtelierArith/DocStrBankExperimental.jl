```julia
animateStateMachineHistoryByTime(
    hist;
    frames,
    folder,
    title,
    show,
    startT,
    stopT,
    rmfirst,
    vertColor
)

```

各状態遷移機の希望するフレームを時間的に同期させて同時に描画します。これらの画像は、同時に実行されている状態遷移機のデバッグや比較を容易にするために、同期した横並びのビデオに生成することができます。
