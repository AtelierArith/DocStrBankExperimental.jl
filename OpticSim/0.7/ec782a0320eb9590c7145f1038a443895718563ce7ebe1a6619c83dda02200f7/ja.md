```
traceMT(system::AbstractOpticalSystem{T}, raygenerator::OpticalRayGenerator{T}; printprog = true, test = false)
```

`system`を`raygenerator`によって生成された光線でトレースします。可能な限り多くのスレッドを使用します。オプションで、進行状況をREPLに印刷することができます。`test`が有効になっている場合、フレネル反射は無効になり、電力分布は正しくありません。`outpath`が指定されている場合、結果はこのパスに保存されます。

すべてのスレッドからの累積検出器画像を返します。
