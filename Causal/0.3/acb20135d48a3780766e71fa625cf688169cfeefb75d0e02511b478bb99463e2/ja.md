```julia
simulate!(
    model,
    clock;
    simdir,
    simprefix,
    simname,
    logtofile,
    loglevel,
    reportsim,
    withbar,
    breakpoints
)

```

`model`をシミュレートします。`simdir`はシミュレーションファイルが保存されるディレクトリのパスです。`simprefix`はシミュレーション名`simname`のプレフィックスです。`logtofile`が`true`の場合、シミュレーションのログファイルが作成されます。`loglevel`はログのレベルを決定します。`reportsim`が`true`の場合、モデルコンポーネントがファイルに保存されます。`withbar`が`true`の場合、シミュレーションの進行状況を示すプログレスバーがコンソールに表示されます。
